---
title: "newbie trying to get NVidia Video Card Working in Linuxmint"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by gribbsy on 2010-01-08
Hello.  I just bought a new pc.  It has plenty of hard drive space and ram with a 2.6GHz processor.
I'm trying to run a dual-boot with Windows 7 and Linuxmint.

I need some help as to how I go about installing my video driver.   I have tried combinations of the following:
-clicking on the taskbar icon that says "restricted drivers are available" and enabling the drivers
-going to Software Manager/Drivers and choosing to install "NVidia 3D Drivers"

My efforts so far have only resulted in the following behavior:
   -  The screen changes from color into black-and-white and becomes unresponsive except to close it out
   -  The screen freezes up completely forcing me open up a terminal to kill the offending process  (which turns out to be firefox)

The next thing I would like to try is to just go to the Nvidia website and downloading and installing the driver from there.  It's a BIN file with a "run" extension.  So I entered the command "chmod +x NVIDIA-Linux-x86-190.53-pkg1.run" followed by the command "./NVIDIA-Linux-x86-190.53-pkg1.run".  But I get an error that says the following:  

**ERROR: You appear to be running an X server; please exit X before installing**. 

WHAT IS AN X SERVER?  HOW DO I CLOSE IT?? I've got nothing unusual open.  Maybe a web page.  I've tried closing out of everything except the terminal and I still get the same message.  

Thanks for the help

---

### Post by darco on 2010-01-08
Hey fellow mint user!....
Check out this link.....it works fine,,,

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)


good luck

darco

---

### Post by gribbsy on 2010-01-10
Thanks for the help.  It turned out to be one of my firefox add-ons that was the culprit.  It is a password manager tool called "Last Pass".  Whenever I tried to log onto my Lastpass account, the computer would freeze up .  I eventually signed up for the service under another name and it worked.  Then I simply logged off, and logged back in under my old name.

---

