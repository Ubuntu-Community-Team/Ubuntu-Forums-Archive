---
title: "Regarding PTAMM installation"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by rahul_budhiraja on 2010-03-28
Dear All,

       I am trying to install the PTAMM source ([http://www.robots.ox.ac.uk/~bob/research/research_ptamm.html),I]("http://www.robots.ox.ac.uk/%7Ebob/research/research_ptamm.html%29,I") am a newbie to linux so pls be gentle to my qns :)

The instructions to the installation are within the folder itself and also I additionally followed the instructions available on [[http://www.minus-reality.com/?p=1]](http://www.minus-reality.com/?p=1]) Minus Reality.

Unfortunately I am stuck and badly stuck on the part when trying to compile the make file :

I press make on the console and I get the following errors:

g++ -o PTAMM main.o GLWindow2.o GLWindowMenu.o VideoSource_Linux_DV.o System.o ATANCamera.o KeyFrame.o MapPoint.o Map.o SmallBlurryImage.o ShiTomasi.o HomographyInit.o MapMaker.o Bundle.o PatchFinder.o Relocaliser.o MiniPatch.o MapViewer.o ARDriver.o EyeGame.o Tracker.o tinyxml.o tinyxmlerror.o tinyxmlparser.o MapLockManager.o MD5.o MD5Wrapper.o MapSerializer.o Games.o Utils.o ShooterGame.o ShooterGameTarget.o ModelsGame.o ModelBrowser.o ModelControls.o MGButton.o Model3ds.o ModelsGameData.o -L MY_CUSTOM_INCLUDE_PATH -lcvd -lGVars3 -l3ds
/usr/bin/ld: cannot find -lcvd
collect2: ld returned 1 exit status

I understand that I do not have libcvd (which is a nexternal library wich i installed using apt-get) but unfortunately I am not able to resolve the error as I have already installed libcvd in the /usr/local/include folder but still the error persists.I installed the folder multiple times,placed the libcvd folder in my directory also and tried installing it but unfortunately I am stuck.!

If anyone could give me guidance on this issue I shall be highly grateful to them .btw I am using ubuntu 9.10.

Cheers!

Rahul

---

