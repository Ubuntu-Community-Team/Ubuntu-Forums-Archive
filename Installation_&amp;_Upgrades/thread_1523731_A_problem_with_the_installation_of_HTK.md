---
title: "A problem with the installation of HTK"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by bejimed on 2010-07-04
I had the ubuntu 10.04 and iwant to install HTK 3

I run succesfly ./configure , make all , make install but  I had a problem testing the HTKDemo like showed below :  
   
Number of owners = 1
 SegLab   :  S
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
16 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -804.22485
Iteration 2: Average LogP =  -786.82153  Change =    17.40332
Iteration 3: Average LogP =  -786.21497  Change =     0.60657
Iteration 4: Average LogP =  -786.21503  Change =    -0.00006
Estimation converged at iteration 5
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM C
HInit -A -i 10 -L labels/bcplabs/mon -l C -o C -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/C data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/C . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  C
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
90 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -531.87134
Iteration 2: Average LogP =  -527.31677  Change =     4.55458
Iteration 3: Average LogP =  -526.60242  Change =     0.71439
Iteration 4: Average LogP =  -526.32343  Change =     0.27898
Iteration 5: Average LogP =  -526.26605  Change =     0.05737
Iteration 6: Average LogP =  -526.24451  Change =     0.02152
Iteration 7: Average LogP =  -526.23560  Change =     0.00892
Iteration 8: Average LogP =  -526.23364  Change =     0.00196
Iteration 9: Average LogP =  -526.22852  Change =     0.00513
Iteration 10: Average LogP =  -526.22852  Change =     0.00000
Estimation converged at iteration 11
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM V
HInit -A -i 10 -L labels/bcplabs/mon -l V -o V -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/V data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/V . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  V
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
68 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -599.68671
Iteration 2: Average LogP =  -592.98328  Change =     6.70342
Iteration 3: Average LogP =  -592.21442  Change =     0.76883
Iteration 4: Average LogP =  -591.48163  Change =     0.73280
Iteration 5: Average LogP =  -591.14313  Change =     0.33848
Iteration 6: Average LogP =  -591.08777  Change =     0.05535
Iteration 7: Average LogP =  -591.05005  Change =     0.03773
Iteration 8: Average LogP =  -590.98999  Change =     0.06004
Iteration 9: Average LogP =  -590.98560  Change =     0.00441
Iteration 10: Average LogP =  -590.98558  Change =     0.00001
Estimation converged at iteration 11
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM N
HInit -A -i 10 -L labels/bcplabs/mon -l N -o N -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/N data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/N . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  N
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
16 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -398.18735
Iteration 2: Average LogP =  -395.48718  Change =     2.70016
Iteration 3: Average LogP =  -395.26947  Change =     0.21771
Iteration 4: Average LogP =  -395.17661  Change =     0.09286
Iteration 5: Average LogP =  -395.17661  Change =     0.00000
Estimation converged at iteration 6
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM L
HInit -A -i 10 -L labels/bcplabs/mon -l L -o L -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/L data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/L . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  L
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
25 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -424.39636
Iteration 2: Average LogP =  -420.31281  Change =     4.08355
Iteration 3: Average LogP =  -419.43475  Change =     0.87804
Iteration 4: Average LogP =  -419.35437  Change =     0.08038
Iteration 5: Average LogP =  -419.32385  Change =     0.03050
Iteration 6: Average LogP =  -419.32387  Change =    -0.00001
Estimation converged at iteration 7
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM S
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l S -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/S data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/S . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  S
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
16 Examples loaded, Max length = 20, Min length = 13
Ave LogProb at iter 1 = -785.97754 using 16 examples
Ave LogProb at iter 2 = -799.75970 using 16 examples  change =  -13.78217
Ave LogProb at iter 3 = -799.59235 using 16 examples  change =    0.16736
Ave LogProb at iter 4 = -799.49408 using 16 examples  change =    0.09827
Ave LogProb at iter 5 = -799.43396 using 16 examples  change =    0.06012
Ave LogProb at iter 6 = -799.36908 using 16 examples  change =    0.06488
Ave LogProb at iter 7 = -799.31201 using 16 examples  change =    0.05707
Ave LogProb at iter 8 = -799.28625 using 16 examples  change =    0.02576
Ave LogProb at iter 9 = -799.26813 using 16 examples  change =    0.01813
Ave LogProb at iter 10 = -798.93494 using 16 examples  change =    0.33319
Estimation aborted at iteration 10

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM C
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l C -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/C data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/C . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  C
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
90 Examples loaded, Max length = 25, Min length = 3
Ave LogProb at iter 1 = -525.97860 using 90 examples
Ave LogProb at iter 2 = -530.95642 using 90 examples  change =   -4.97785
Ave LogProb at iter 3 = -530.95356 using 90 examples  change =    0.00286
Ave LogProb at iter 4 = -530.95312 using 90 examples  change =    0.00043
Ave LogProb at iter 5 = -530.95304 using 90 examples  change =    0.00009
Estimation converged at iteration 5

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM V
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l V -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/V data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/V . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  V
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
68 Examples loaded, Max length = 28, Min length = 3
Ave LogProb at iter 1 = -590.79446 using 68 examples
Ave LogProb at iter 2 = -600.09358 using 68 examples  change =   -9.29914
Ave LogProb at iter 3 = -600.08226 using 68 examples  change =    0.01131
Ave LogProb at iter 4 = -600.07560 using 68 examples  change =    0.00668
Ave LogProb at iter 5 = -600.07071 using 68 examples  change =    0.00491
Ave LogProb at iter 6 = -600.06859 using 68 examples  change =    0.00215
Ave LogProb at iter 7 = -600.06830 using 68 examples  change =    0.00030
Ave LogProb at iter 8 = -600.06801 using 68 examples  change =    0.00028
Ave LogProb at iter 9 = -600.06801 using 68 examples  change =   -0.00002
Estimation converged at iteration 9

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM N
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l N -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/N data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/N . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  N
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
16 Examples loaded, Max length = 13, Min length = 4
Ave LogProb at iter 1 = -395.06061 using 16 examples
Ave LogProb at iter 2 = -403.25287 using 16 examples  change =   -8.19226
Ave LogProb at iter 3 = -403.23053 using 16 examples  change =    0.02234
Ave LogProb at iter 4 = -403.20822 using 16 examples  change =    0.02231
Ave LogProb at iter 5 = -403.19427 using 16 examples  change =    0.01395
Ave LogProb at iter 6 = -403.19070 using 16 examples  change =    0.00357
Ave LogProb at iter 7 = -403.19000 using 16 examples  change =    0.00070
Ave LogProb at iter 8 = -403.18976 using 16 examples  change =    0.00024
Ave LogProb at iter 9 = -403.18970 using 16 examples  change =    0.00006
Estimation converged at iteration 9

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM L
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l L -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/L data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/L . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  L
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
25 Examples loaded, Max length = 14, Min length = 4
Ave LogProb at iter 1 = -419.20465 using 25 examples
Ave LogProb at iter 2 = -425.78465 using 25 examples  change =   -6.58000
Ave LogProb at iter 3 = -425.76195 using 25 examples  change =    0.02268
Ave LogProb at iter 4 = -425.74531 using 25 examples  change =    0.01665
Ave LogProb at iter 5 = -425.73094 using 25 examples  change =    0.01436
Ave LogProb at iter 6 = -425.72137 using 25 examples  change =    0.00956
Ave LogProb at iter 7 = -425.71652 using 25 examples  change =    0.00485
Ave LogProb at iter 8 = -425.71375 using 25 examples  change =    0.00277
Ave LogProb at iter 9 = -425.71164 using 25 examples  change =    0.00210
Ave LogProb at iter 10 = -425.71000 using 25 examples  change =    0.00164
Estimation aborted at iteration 10

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Iteration 1 of Embedded Re-estimation
HERest -A -w 3 -v 0.05 -C toolconfs/herest.conf -u tmvw -d hmms/hmm.1 -D -M hmms/hmm.2 -L labels/bcplabs/mon -t 2000.0 -T 1 lists/bcplist data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
#                 BINARYACCFORMAT              TRUE
#                 KEEPDISTINCT                TRUE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

HERest  ML Updating: Transitions Means Variances 

 System is PLAIN
5 Logical/5 Physical Models Loaded, VecSize=26
Pruning-On[2000.0]
 Processing Data: tr1.mfc; Label tr1.lab
 Utterance prob per frame = -5.980291e+01
 Processing Data: tr2.mfc; Label tr2.lab
 Utterance prob per frame = -5.937575e+01
 Processing Data: tr3.mfc; Label tr3.lab
 Utterance prob per frame = -5.935562e+01
 Processing Data: tr4.mfc; Label tr4.lab
 Utterance prob per frame = -5.919727e+01
 Processing Data: tr5.mfc; Label tr5.lab
 Utterance prob per frame = -5.789522e+01
 Processing Data: tr6.mfc; Label tr6.lab
 Utterance prob per frame = -5.910780e+01
 Processing Data: tr7.mfc; Label tr7.lab
 Utterance prob per frame = -5.739422e+01
Total 27 floored variance elements in 15 different mixes
Saving hmm's to dir hmms/hmm.2
Reestimation complete - average log prob per frame = -5.900193e+01
     - total frames seen          = 1.811000e+03

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
                  BINARYACCFORMAT              TRUE
                  KEEPDISTINCT                TRUE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D

cp: la cible `hmms/tmp' n'est pas un répertoire


Iteration 2 of Embedded Re-estimation
HERest -A -w 3 -v 0.05 -C toolconfs/herest.conf -u tmvw -d hmms/tmp -D -M hmms/hmm.2 -L labels/bcplabs/mon -t 2000.0 -T 1 lists/bcplist data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
#                 BINARYACCFORMAT              TRUE
#                 KEEPDISTINCT                TRUE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

  ERROR [+5010]  InitSource: Cannot open source file hmms/tmp/C
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2321]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HERest
cp: la cible `hmms/tmp' n'est pas un répertoire


Iteration 3 of Embedded Re-estimation
HERest -A -w 3 -v 0.05 -C toolconfs/herest.conf -u tmvw -d hmms/tmp -D -M hmms/hmm.2 -L labels/bcplabs/mon -t 2000.0 -T 1 lists/bcplist data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
#                 BINARYACCFORMAT              TRUE
#                 KEEPDISTINCT                TRUE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

  ERROR [+5010]  InitSource: Cannot open source file hmms/tmp/C
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2321]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HERest
cp: la cible `hmms/tmp' n'est pas un répertoire
Removed 0 files from hmms/tmp

Testing on the training set
Can't open test
root@beji-mohamed-desktop:~/Téléchargements/samples/HTKDemo#
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9537575") 		 		 		 		 		 		 		 			 		 		 		 	       	 	 		bejimed 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=1105359") 	 	 		[Send a private message to bejimed]("http://ubuntuforums.org/private.php?do=newpm&u=1105359") 	 	 	 	 		[Find More Posts by bejimed]("http://ubuntuforums.org/search.php?do=finduser&u=1105359")

---

