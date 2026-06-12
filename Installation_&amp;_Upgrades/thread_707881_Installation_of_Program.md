---
title: "Installation of Program"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by insenlysen on 2008-02-25
Hi

I am trying to install a program called FlameMaster for my final year project. I am getting the following error while trying to run the installation bash file
start installing FlameMan
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c BroadeningFactors.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c FlameMasterMain.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c FlameUtilities.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TFlame.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TInputData.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TProperties.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TReaction.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c SteadyStates.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TSpecies.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TSoot.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TPAH.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TCountDiffFlameMix.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TCountDiffFlameCont.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TCountDiffFlameSim.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TCountDiffFlamePhys.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TCountDiffPhysEigen.C
g++  -x c++ -O3 -I/home/photon/FlameMaster/FlameManLibs -DLINUXGXX -c TFlameSheet.C
TFlameSheet.C: In member function ‘void TFlameSheet::InitTFlameSheet()’:
TFlameSheet.C:47: error: ‘FlameSheetPostIter’ was not declared in this scope
make: *** [TFlameSheet.o] Error 1

Any Suggestions?

---

### Post by sivaji_siv on 2008-05-13
Hi,

Could you please tell me whether we can can install flamemaster in Windows? or it is only in LINUX or UNIX?

thanks

---

### Post by zenwalker on 2008-05-13
Is the package src code in C lang and shud be compiled from C compiler rather than from c++? Try to use cc instread g++ or c++. 

Plus read the README or INSTALL txt files if present of try to get the info abt the ver of compiler and external libs needed to compile that package.

---

### Post by sivaji_siv on 2008-05-15
Hi,
Thanks for your suggestion, i am trying install this flamemaster in ubuntu, i got gcc compiler and g++, libstdc++ files.. but i am unable to install it because of ntlmaps not installed properly in PC. and it is asking for yacc but i am able to get byacc.

couldyou explain how to install ntlmaps properly on my computer first. i am using ubuntu7.1 version
thank you

---

