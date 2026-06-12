---
title: "Unable to access Ubuntu install"
date: 2016-11-09
forum: Installation &amp; Upgrades
---

### Post by henry50 on 2016-11-09
I recently installed Ubuntu 14.04 LTS alongside windows 8.1 (the 16.04 LTS install refused to work, and I thought it would be faster to update Ubuntu once it is already working) and it seemed to work fine, after it finished it asked me to restart my computer. It booted into windows, as that is the native OS, but I have had no luck finding out how to switch between the two systems. I am not able to access the Ubuntu files in any way from windows, however I was able to access my Ubuntu partition from the trial mode on the Ubuntu install disc, I don't know if that could be in any way useful, but I thought I should mention it.

---

### Post by ubfan1 on 2016-11-10
Did you follow the instructions at
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Did you turn off the Windows power option fastboot, and make boot speed normal (not fast) or some non-zero value (so you can hit a function key at power-on if necessary)?
Did you install in UEFI mode?  Install media boots both UEFI and legacy, which is determined by your selections in the BIOS/UEFI settings.  Install Ubuntu in the same mode Windows is installed.  If you got your machine from a major manfacturer with Windows 8+ preinstall, it is in UEFI mode.  Upgraded from Win 7, it's probably not in UEFI mode.

---

### Post by henry50 on 2016-11-10
I can't seem to find any options for boot speed, but I already have enough time to access the boot menu. I'm not sure what mode I installed Ubuntu in, but I think it is probably UEFI (the same as Windows on my computer). Everything seems to indicate that Ubuntu installed fine, but I can't access it in any way.

---

### Post by yancek on 2016-11-10
The problem you indicate is often the result of installing one system UEFI and the other MBR.  Almost always resutls in either windows only booting or Linux only booting.  Take a look at the link below on dual booting Ubuntu and windows UEFI and compare it to what you did.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you are still unable to resolve the issue, you need to post more detailed information which you can get by using the boot repair script which you can download and run from the isntallation media.  Select the Create BootInfo Summary option and post a link to the output.  Do not try to run any repairs.  Someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You won't be able to access your Ubuntu (or any Linux) files from windows without installing some third party software on windows.  That is by design from microsoft.

---

### Post by henry50 on 2016-11-10
I know understand what my problem is, but not how to fix it. Because my Ubuntu partition was created outside of windows, windows refuses to let me change or edit it. As I mentioned before, the only way that I currently have to access my Ubuntu partition is through the trial mode, but in that, I lack admin privileges. Unfourtunatley that means that I cannot uninstall Ubuntu and change the install options, I also have too little unalocated space to install Ubuntu on that, and then delete the old partition from there.

I just realized that I can delete the partition, so disregard the rest of this reply for now, but that may not work.

I deleted the partition and reinstalled Ubuntu, but never got the option to change into UEFI mode. I's sure there is a way, but I could not find it.

---

### Post by ubfan1 on 2016-11-10
The decision which mode the install media uses is made before it is booted -- your settings in the BIOS/UEFI settings determine how the install media boots and installs.  Each machine is different, so I can only generally suggest what to set:  You might have a UEFI enabled switch, a legacy first or UEFI first toggle, or a "compatibility" mode (CMS) switch (which is not a good way since instead of you selecting the boot mode, it lets the machine decide how to boot).  The grub screen will  be black for a UEFI boot, or purple for a legacy boot.

---

### Post by oldfred on 2016-11-10
Do not try to use Windows to do anything with Linux. Only delete a Linux partition from a Linux live installer in live mode, and before you do that make sure Windows is default boot.

Follow the adage:
Windows tools for Windows and Linux tools for Linux.
Although a few minor Windows fixes can be done from Linux.

Most systems have a one time boot key for the UEFI boot menu. Often f10 or f12 check your manual. 
Even if Ubuntu is BIOS boot and Windows UEFI boot, you still can boot from UEFI boot menu. But really need to have Ubuntu in same boot mode as Windows.

---

