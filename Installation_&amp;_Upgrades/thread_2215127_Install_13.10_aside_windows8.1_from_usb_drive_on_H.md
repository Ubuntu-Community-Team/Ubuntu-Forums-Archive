---
title: "Install 13.10 aside windows8.1 from usb drive on HP ultrabook"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by simon27 on 2014-04-04
[COLOR=#37404E][FONT=lucida grande]Hello,  The attached photos shows what I am getting when halfway installing ubuntu aside win8. The partition table is empty, and if I click install I will get an error msg, saying "no root file system defined". A step was missing from the installation process, which asks if ubuntu overwrite win8 or dual with win8, that step never showed up and just skipped not under my control. Certainly something is wrong here, Can someone help?





[/FONT][/COLOR]

---

### Post by ubfan1 on 2014-04-04
On the Windows side, did you turn off dynamic partitions, raid, and fast boot?  You should see disk partitions if nothing is interferring.

---

### Post by grahammechanical on 2014-04-04
It seems that the installer has gone straight into the Something Else option but cannot give you any partition information. I can only guess. It is possible that the installer is not able to read the Windows partitions because they are in a Microsoft proprietary format.

Having Windows 8 means that the boot system is UEFI. This may help. I am not sure.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

Edit: The second and third answers here might be of use to you.

[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)

Regards.

---

### Post by fantab on 2014-04-04
Read thoroughly through the first link *grahammechanical* shared with you. You MUST know what UEFI is and what GPT is. 
You have to disable certain 'features' in Windows 8.1 for dual-boot to work, like:
***FastStartup***- This keeps Windows in 'Hibernation' and won't really shut-down the PC when you use the 'shutdown' button.
***Fastboot***- This is a UEFI feature and sometimes it needs to be disabled. You can reactivate it later after installing Ubuntu.
***IntelSRT***- Found on Intel Mobos. This feature usually comes activated when there is pre-installed SSD which is used for 'cacheing'. It used some sort of hybrid RAID, and is painful to install Ubuntu with IntelSRT/IntelRST enabled.
***Secure Boot***- Ubuntu can install and work with 'Secure Boot' enabled. However we advice that you disable it.

Make yourself a Windows REPAIR Disc.

Read Here for more info on how go about managing Hard disk...
[http://ubuntuforums.org/showthread.php?t=2213992&p=12971982#post12971982](http://ubuntuforums.org/showthread.php?t=2213992&p=12971982#post12971982)



If for any reason you have doutbts then; Boot with Ubuntu DVD/USB and 'Try Ubuntu Without installing'. Open Terminal [ctrl+alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by simon27 on 2014-04-06
Thanks, you guys rock !

Problem solved and this one helps
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)

---

