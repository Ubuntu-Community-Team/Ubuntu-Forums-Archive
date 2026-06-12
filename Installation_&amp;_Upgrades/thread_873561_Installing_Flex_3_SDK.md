---
title: "Installing Flex 3 SDK?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by itsjareds on 2008-07-29
I am trying to install Adobe Flex 3 SDK on Ubuntu, but it's pretty tricky how to install it (for me). The installation docs aren't very clear.

This is what it says:
> 1. Download Flex SDK ZIP file from the Adobe website.

   2. Create a directory to contain Flex SDK.

   3. Extract the Flex SDK ZIP file to this directory. The Flex SDK contains the following directories:
          * /ant &#8212; Contains Flex Ant Tasks.
          * /asdoc &#8212; Contains helper files for the ASDoc tool that creates HTML documentation from your MXML and ActionScript source code.
          * /bin &#8212; Contains the mxmlc, compc, asdoc, and fdb utilities. The bin directory also contains the jvm.config file, which specifies Java settings that you can modify, if necessary.
          * /frameworks &#8212; Contains compiled framework classes, configuration files, and framework source code.
          * /lib &#8212; Contains JAR files used by the utilities.
          * /runtimes &#8212; Contains installers for the Adobe AIR runtime inside the air directory and installers for debug versions of Flash Player 9 inside the player directory.
          * /samples &#8212; Contains sample applications.
          * /templates &#8212; Contains HTML templates for Flash Player detection and browser integration and inside the air folder, a sample Adobe AIR application.xml file.

   4. Ensure that the Java Runtime Environment (JRE) is installed on the computer and that the java_home/bin directory is defined in the system path. JRE 1.4, 1.5, or 1.6 is required. For 1.4, JRE 1.4.2_06 or later is required.

   5. Install the appropriate debug Flash Player from the install_root/runtimes/player/platform directory.

   6. (Optional) When the Flash Player installation finishes, restart your computer to ensure that the updated Flash Player browser plug-in is enabled.

   7. Continue by reviewing the explorer sample. To run the explorer sample, you must first compile it running the install_root/samples/explorer/build.bat (Windows) or install_root/samples/explorer/build.sh (UNIX and Mac OS X) files. For more information on the Flex compilers, see the "Using the Flex Compilers" chapter in the Building and Deploying Flex Applications manual.



I have everything correct for steps 1-4, but on step 5 I am confused. I go to ~/Flex/runtimes/player/lnx, and I only see two tar.gz files. One is named install_flash_player_9.tar.gz, and the other is flashplayer.tar.gz. I assume that I should install the first one, so I go to extract it. 

All that is in this file is a file called flashplayer-installer and libflashplayer.so

Clicking both of them does nothing, what should I do? Or what program should I run them with?

---

### Post by itsjareds on 2008-07-29
bump :\

---

### Post by izak on 2008-08-05
Hmm, this is not comforting: I also want to install the flex3 sdk, but had great difficulty getting flash to work. 

Using the multimedia howto sticky thread  ([http://ubuntuforums.org/showthread.php?t=766683)specifically](http://ubuntuforums.org/showthread.php?t=766683)specifically) the torubleshooting section for adobe flash will hopefully work... I'm trying it out now.

---

### Post by izak on 2008-08-05
curses! now I have messed up my working flash installation and I can't get the it working again... I'm off to post in that thread...

---

### Post by izak on 2008-08-05
@ itsjareds: you should extract both files here. flashplayer-installer is a bash script; I don't know if it will work for you; for me it says 'unsupported achitecture /x86_64/'. If you want to try it simpy open a console at that location and run

sudo ./flashplayer_installer

this should then hopefully extract and install libflashplayer.so in all the right places. If it does not, your guess is as good as mine: head tot the comprehensive multimedia thread and see if those instructions help you at all. 

The flashplayer.tar.gz. when extracted, creates a standalone flashplayer (just double click the extracted file). You can open .swf files and play them using this. It also has a menu item called debug, which will hopefully prove usefull.

Please report back on your success. My flash player is still not working at all :(

---

