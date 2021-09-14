# detect-af
A project to analyse the patterns in ECG data, and to train machine learning models to automatically detect Atrial Fibrillation.

The approach to this problem involved the application of machine learning (ML) models to a set of electrocardiogram (ECG) data with labelled examples of AF and non-AF periods. Relevant features for inclusion were identified from the literature on AF detection, and were used to fit decision trees and eXtreme Gradient Boosted (XGBoost) models.

#### Background
Atrial fibrillation (AF) is a type of heart rhythm disturbance, and is the most common sustained arrhythmia \[1\]. It has been shown that AF is linked to a substantial increase in the risk of morbidity and mortality \[2\]. Automated AF detection already has some clinical and consumer applications, such as smartwatches with built-in ECG \[3\], \[4\]. 

#### Data
The dataset used in this study was preprocessed ECG data from the Erasmus Medical Centre in Rotterdam of the department electrophysiology. It consisted of 804 files of 24-hour recordings, where each row represents one beat and the interval between R peaks (RRI) is provided in milliseconds (ms). Annotations were added to the beats by physicians to indicate the times where the patient was experiencing Atrial Fibrillation.

#### Method
The beats were first grouped into 30-beat segments. Then, relevant features were identified in the literature, including root mean square of successive differences (RMSSD), Shannon entropy, and turning point ratio \[5\], histograms of the RRI \[6\], histograms of the differences between successive RRI \[7\], and finally summary statistics such as mean, min, variance, etc. These features were then used to train Decision Tree and XGBoost models.

<kbd><img src="figures/Entropy Histograms.png" width=100px height=100px /></kbd>
<kbd><img src="figures/RMSSD Histogram.png" width=100px height=100px /></kbd>
<kbd><img src="figures/TPR Histogram.png" width=100px height=100px /></kbd>

#### Results
Ultimately, a Sensitivity of 97.2% and Specificity of 99.3% was achieved when predicting whether each 30-beat segment is Atrial Fibrillation or not, improving on the older studies taking purely statistical or heuristic approaches, and comparable to studies involving the use of deep learning approaches \[8\] (this study used a different dataset, however, so the results can not be compared directly).

#### References
\[1\] Fuster Valentin et al., ‘2011 ACCF/AHA/HRS Focused Updates Incorporated Into the ACC/AHA/ESC 2006 Guidelines for the Management of Patients With Atrial Fibrillation’, J. Am. Coll. Cardiol., vol. 57, no. 11, pp. e101–e198, Mar. 2011, doi: 10.1016/j.jacc.2010.09.013.
\[2\] E. J. Benjamin, P. A. Wolf, R. B. D’Agostino, H. Silbershatz, W. B. Kannel, and D. Levy, ‘Impact of Atrial Fibrillation on the Risk of Death’, Circulation, vol. 98, no. 10, pp. 946–952, Sep. 1998, doi: 10.1161/01.CIR.98.10.946.
\[3\] Withings, ‘Move ECG – ECG Monitor & Activity watch’, Withings.com, 2020. /us/en/move-ecg (accessed Apr. 06, 2021).
\[4\] Samsung, ‘Electrocardiogram Monitoring App’, Samsung US Newsroom, Sep. 23, 2020. https://news.samsung.com/us/health-electrocardiogram-monitoring-app-ECG-galaxy-watch3-active2 (accessed Apr. 06, 2021).
\[5\] S. Dash, K. H. Chon, S. Lu, and E. A. Raeder, ‘Automatic real time detection of atrial fibrillation’, Ann. Biomed. Eng., vol. 37, no. 9, pp. 1701–1709, Sep. 2009, doi: 10.1007/s10439-009-9740-z.
\[6\] K. Tateno and L. Glass, ‘A method for detection of atrial fibrillation using RR intervals’, in Computers in Cardiology 2000. Vol.27 (Cat. 00CH37163), Sep. 2000, pp. 391–394, doi: 10.1109/CIC.2000.898539.
\[7\] K. Tateno and L. Glass, ‘Automatic detection of atrial fibrillation using the coefficient of variation and density histograms of RR and ΔRR intervals’, Med. Biol. Eng. Comput., vol. 39, no. 6, pp. 664–671, Nov. 2001, doi: 10.1007/BF02345439.
\[8\z] Y. Xia, N. Wulan, K. Wang, and H. Zhang, ‘Detecting atrial fibrillation by deep convolutional neural networks’, Comput. Biol. Med., vol. 93, pp. 84–92, Feb. 2018, doi: 10.1016/j.compbiomed.2017.12.007.
