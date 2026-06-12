---
title: "Ubuntu hardware detection"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by lm77054 on 2011-11-02
Hi All:  I've decided to start the migration from Windows to UBUNTU.  However, I've decided not to make the leap all at once.  I'll be running UBUNTU as a Windows App for probably six months or so first.  Now, my wife and I both have laptops, same manufacturer, but different models.  So the hardware isn't 100% the same.  I know that I can copy C:\UBUNTU between the computers, and manually update the BOOT.INI file to allow the boot selection.  However, my question is this.  If I copy the C:\UBUNTU from my computer, to my wife's, and modify the boot.ini, will UBUNTU detect the new hardware and automatically update the hardware configuration?  If not, is there an easy way to force UBUNTU to detect the changes, without doing a full build on hers.  My wife's computer and mine (Windows) are built up with the same basic configuration, and the same will be true for UBUNTU.  So by building the basic UBUNTU on my system, as a Windows APP, I can copy the config between systems.  Thanks loads!

---

### Post by Frogs Hair on 2011-11-02
If you are running a Wubi installation , Ubuntu can be moved to its own partition , but there is some work involved . [http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

Ubuntu should detect your hardware , but check wireless driver compatibility if applicable . [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

When using wubi , Ubuntu is running inside the Windows partition and using the Windows boot loader , but is not running as an Windows application . The drive designations are completely different than Windows  
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
 
For help with Wubi .[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

