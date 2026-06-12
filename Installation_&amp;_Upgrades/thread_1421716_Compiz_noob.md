---
title: "Compiz noob"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by Durduman on 2010-03-04
Hello! I followed these steps in how to install compiz pack ( I guess )  and found myself in a dilemma. The steps are:



__________________________________ 
**CODE**
sudo apt-get -y remove compiz-core desktop-effects



Leave the terminal open and go to *System -> Administration -> Software Sources*, click on the second tab (Third-Party Software), then click on the "Add" button and paste the following code:

**CODE**
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy



Click the "Add Source" button after you pasted the above code and do the same for the following code:

**CODE**
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy



**Don't close the Software Sources window yet!**

In the terminal window, type:

**CODE**
wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)



**CODE**
sudo apt-key add DD800CD9.gpg



Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Copy/Paste the following lines in the terminal window:

**CODE**
sudo apt-get update

sudo apt-get -y upgrade



**FOR GNOME USERS:**

**CODE**
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf



**FOR KDE USERS:**

**CODE**
sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig



Now, if everything was correctly installed and you didn't encounter errors, press ALT+F2 and type:

**CODE**
compiz --replace



That's it! Enjoy the latest 3D eye candy effects on your (K)Ubuntu OS.


____________________________________________



my problem occurs when I do compiz --replace in terminal
it halts in this poin ( over 15 min til now ) .



urdu@durdu-laptop:~$ sudo compiz --replace
[sudo] password for durdu: 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I tried it earlier without sudo and the same problem occured.
 
thank you in advance!

---

### Post by adam22 on 2010-03-04
I don't understand what those directions are for....I'll take a guess and say there's newer and unsupported effects you're trying to install. 

I know this isn't what you want, but perhaps take a look at my guide and see if it will help you: [http://ubuntuforums.org/showthread.php?t=1414548](http://ubuntuforums.org/showthread.php?t=1414548)

You don't need that other crap, in my opinion. But, from what I can tell, that last code does not go in terminal...it says push alt+F2 which brings up the "Run Application" window....?

---

### Post by Durduman on 2010-03-06
thank you ... followed steps and instaled compiz... thx adam

---

