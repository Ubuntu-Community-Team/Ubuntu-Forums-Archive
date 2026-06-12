---
title: "Instillation has no type windows 10"
date: 2020-04-20
forum: Installation &amp; Upgrades
---

### Post by tiana142 on 2020-04-20
I currently cannot install Unbutu because there are no instillation types when I try to install it. The +- buttons always crash the instillation window.
I am trying to dual install version 18.04.4 with windows 10, it needs to install using UEFI since that is what windows is on. I am also installing off a USB.
I have created a partition through windows that has over 50GB on it and it never shows up, when I go into Gparted in the only partition that I can see is the USB drive.
I have already disabled fastboot, checked to see if I have a dynamic disk(I do not), and checked to see if any of my partitions are damaged.
I tried to convert my laptop to legacy boot and when I did that I was able to at least have instillation options, but I learned quickly that for dual I need Ubuntu to be UEFI.
I have spent hours trying to solve this issue through other message boards without luck, please help.

---

### Post by guiverc on 2020-04-20
Did you verify the downloaded ISO to ensure it was perfect?  ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) and then the write to your install media ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) where CD refers to any media used, ie. CD/DVD/hdd/ssd/thumb-drive/flash-card/etc)

These checks take a minute or so, but save hours-days of problem solving if either was flawed (thus I think of it as cheap insurance).

---

### Post by cmcanulty on 2020-04-20
I've had luck when the install crashes like this by doing the following.Click try ubuntu instead of install. When it is running click the install icon on desktop and it usually works.

---

### Post by Impavidus on 2020-04-20
Do you have RAID or Intel RST on? Ubuntu needs AHCI. See these threads:
[https://ubuntuforums.org/showthread.php?t=2439921](https://ubuntuforums.org/showthread.php?t=2439921)
[https://ubuntuforums.org/showthread.php?t=2438824](https://ubuntuforums.org/showthread.php?t=2438824)
[https://ubuntuforums.org/showthread.php?t=2440763](https://ubuntuforums.org/showthread.php?t=2440763)

---

### Post by yancek on 2020-04-20
> I have created a partition through windows that has over 50GB on it and it never shows up, 

A standard windows system will not be able to create a partition with a Linux filesystem so it is best to just leave unallocated space on which to create a partition for Ubuntu.
As suggested above, either test the usb on another computer to see if it boots or verify the download as explained on the Ubuntu download page.
Did you turn off fastboot and anything related to hibernation immediately prior to trying to install Ubuntu.  If not, and also if you do get Ubuntu installed you need to be aware that some windows updates will turn hibernation back on and will not ask if you want that nor will you be informed that it is happening.  The fact that the Ubuntu installer does not see the windows partitions is a good indication that it was hibernated.

Not being able to proceed with the installation is likely to be a bad download or a bad write to the usb.

You might read through the Ubuntu documentation on dual booting UEFI with windows at the link below.


  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tiana142 on 2020-04-20
It is an unallocated space. Fastboot and everything is disabled. I have read through that entire help page and nothing I did helped it to install correctly. 
And ive tried doing try instead of install when booting ubuntu.
The flash drive boots up on other laptops and has instillation options, so its an issue with my laptop specifically apperantly

---

### Post by tiana142 on 2020-04-20
[ATTACH=CONFIG]285570[/ATTACH][ATTACH=CONFIG]285571[/ATTACH]
This is what the instillation and the gparted window look like

---

### Post by CelticWarrior on 2020-04-21
Please read and understand post #4.
Also please note that you need to install AHCI support in Windows before changing to that mode in UEFI.

---

