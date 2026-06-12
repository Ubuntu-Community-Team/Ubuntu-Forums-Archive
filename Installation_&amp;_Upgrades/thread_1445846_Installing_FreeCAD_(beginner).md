---
title: "Installing FreeCAD (beginner)"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by bigseb on 2010-04-03
So I downloaded FreeCAD and am reading through the Linux Readme. I am pasting it here --->

How to build and run FreeCAD under Linux 
======================================== 
 
Prerequisites 
------------- 
 
To compile FreeCAD you will need, besides functioning Linux 
and programming tools (like compiler), the following libraries: 
 
o Python ([http://www.python.org](http://www.python.org)), >= 2.5.x 
o boost ([http://www.boost.org](http://www.boost.org)), >= 1.33.1 
o Qt ([http://www.qtsoftware.com](http://www.qtsoftware.com)), >= 4.1.x 
o Coin3D ([http://www.coin3d.org](http://www.coin3d.org)), >= 2.4.x 
o SoQt ([http://www.coin3d.org](http://www.coin3d.org)), >= 1.2.x 
o Xerces-C++ ([http://xml.apache.org/dist/xerces-c/](http://xml.apache.org/dist/xerces-c/)), >= 2.6 
o zlib ([http://www.zlib.net/](http://www.zlib.net/)) 
 
And for the some FreeCAD modules the additional libraries 
o OpenCascade ([http://www.opencascade.org](http://www.opencascade.org)), >= 5.2 
o OpenCV ([http://opencvlibrary.sourceforge.net](http://opencvlibrary.sourceforge.net)), >= 0.9.7 
o ODE ([http://www.ode.org](http://www.ode.org)), >= 0.10.x 
are required. 
 
Note: zlib might be already on your system, as this is a library that is used  
      by a lot of libraries, too. 
 
Note: All libraries listed above must be built as shared library. Refer to their 
      documentation to see how to do. 
 
Note: If possible you should enable thread support for the libraries. At least for 
      Qt thread support is strongly recommended, otherwise you will run into linker 
      errors at build time of FreeCAD. 
 
Note: The package for SoQt for Debian based systems may lack of the soqt.m4 macro file. 
      You should download the file from [www.coin3d.org](www.coin3d.org) and copy it to /usr/share/aclocal. 
 
Note: The package for SoQt (at least for older Debian based systems) is usually built to link  
      against Qt3. This, however, causes a segmentation fault when using with FreeCAD because  
      it links against Qt4 and you get a mixup of Qt3 and Qt4 libraries. 
      To fix this problem you must download the sources from [www.coin3d.org](www.coin3d.org) and run 
      configure with the 'with-qt=DIR' switch specifying the location of Qt4. 
      Probably, it's best to 'make install' the newly built SoQt into a different directory 
      than the installed SoQt to avoid to corrupt your package database and/or to keep other  
      applications working. When configuring FreeCAD you have to use the '--with-soqt=DIR'  
      switch specifying the path of the newly installed SoQt. 
      For newer Debian releases this already solved by a new package that links against Qt4. 
 
Note: For OpenCascade there does not exist an official .deb package for older Debian based systems 
      and many other distributions, so you have to download the latest version from [www.opencascade.org](www.opencascade.org). 
      Install the package normally, be aware that the installer is a java program that requires 
      the official java runtime edition from Sun, not the open-source java (gij) that is bundled 
      with Debian or Ubuntu. Install it if needed: 
 
      sudo apt-get remove gij 
      sudo apt-get install sun-java5-bin 
 
      Be careful, if you use gij java with other things like a browser plugin, they won't work 
      anymore. Now start the installer with 
      java -jar setup.jar 
       
      With Debian Lenny this issue is solved. There is an OpenCascade package currently in the 
      non-free section. 
 
Note: Especially for Debian Etch users the packages for OpenCV (libcv-dev, libcvaux-dev and 
      libhighgui-dev) provides library names with appended version name. 
      In newer Debian versions and other Linux distributions these library names don't have 
      longer embedded the version name. To make the build process working for Debian Etch you 
      either have to replace in the Makefile in src/Mod/Image/App and src/Mod/Image/Gui 
      -lcxcore -lcv -lhighgui -lcvaux \ with 
      -lcxcore0.9.7 -lcv0.9.7 -lhighgui0.9.7 -lcvaux0.9.7 \ or create the symbolic links 
      ln -s libcxcore0.9.7.so libcxcore.so 
      ln -s libcv0.9.7.so libcv.so 
      ln -s libhighgui0.9.7.so libhighgui.so 
      ln -s libcvaux0.9.7.so libcvaux.so 
 
 
During the compilation some Python scripts get executed. So the Python interpreter has 
to work properly. 
 
Optionally, you can build the Qt plugin that provides all custom widgets of FreeCAD 
we need for the Qt Designer. The sources are located under Tools/plugins/widget. 
So far, we don't provide a makefile but calling 'qmake plugin.pro' creates it and 
calling 'make' will create the library libFreeCAD_widgets.so. To make known this library 
to your Qt Designer you have to copy the file to $QTDIR/plugin/designer. 
 
 
Configuration 
------------- 
 
For the build process of FreeCAD we make use of configure scripts. 
To have an overview of all switches type in ./configure --help, first. 
 
You don't need any of these switches unless you have installed a library into a non-standard 
path. In this case make use of the appropriate --with-XXX-include or --with-XXX-lib switches, 
please. (XXX stands for the corresponding library.) 
Of course, for above mentioned problem with SoQt you should use the '--with-soqt=DIR' switch. 
 
Note: To specify FreeCAD's root directory it is recommended to use only the '--prefix' 
switch from the configure script but not the --bindir, --libdir, ... switches, because at startup  
FreeCAD makes assumptions about where its module directories are installed. 
 
 
Installation & Running FreeCAD 
------------------------------ 
 
Once you have built the sources successfully using 'make', with 'make install' you can 
install FreeCAD onto your machine whereever you want. FreeCAD's default root directory  
is $HOME/FreeCAD, so you don't need root privileges therefore. To run FreeCAD go to  
$PREFIX/FreeCAD/bin and type in ./FreeCAD. 
 
Note: In the past there were a lot of problems that the Part workbench couldn't be loaded. 
      The problem is that the system wasn't able to find the OpenCascade library files. 
      To fix this problem you are strongly recommended to add the path of these libraries 
      to LD_LIBRARY_PATH or even to add it to ld.so.conf and run ldconfig.

<--- end of paste

**I will definitely need to be walked through this one. **

Let me see if what I have so far is correct. In addition to what I already have ie. FreeCAD I must also visit each of the 9 sites listed under prerequisites and down the file listed. Not sure if this is an executable or what.

After that it seems to be a case of just tweaking each file (or whatever).

Right so far?

---

### Post by ad_267 on 2010-04-26
FreeCAD is in the Ubuntu 10.04 repositories. The easiest solution is probably to upgrade to 10.04 and install it through the Ubuntu software centre.

---

### Post by bigseb on 2010-04-27
I just got 9.10 up and running... won't I lose everything by upgrading. Also, wouldn't it be better to wait til 10.04 is officially released.

It should be worth notingthat there are two FreeCADs! Two very different products indeed but both are called FreeCAD...

---

### Post by ad_267 on 2010-04-27
You can do an upgrade without reinstalling, so you don't lose anything. There are instructions for upgrading here: [http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2). Running "update-manager -d" tells the update manager to look for a development version. I usually put my home directory on a separate partition so I can do a clean install without losing any of my personal files, I just have to reinstall my software.

And yes it's probably safer to wait until the release, although I've been running 10.04 without any problems for about a week now. The final release is only a couple of days away too so I assume it should be pretty close to ready.

The instructions you have there are for compiling FreeCAD, but they have a .deb package for Ubuntu 9.10 that would be a lot easier to use at [http://sourceforge.net/projects/free-cad/files/FreeCAD%20Linux/FreeCAD%200.9%20R2646/freecad_0.9.2646-1karmic_i386.deb/download](http://sourceforge.net/projects/free-cad/files/FreeCAD%20Linux/FreeCAD%200.9%20R2646/freecad_0.9.2646-1karmic_i386.deb/download).
You should be able to just download that file and open it to install FreeCAD, but I can't test it out at the moment.

And yup, the FreeCAD available in Ubuntu 10.04 is the one you're trying to install. They were talking about getting a new name a while ago but nothing seems to have happened, which is unfortunate.

---

