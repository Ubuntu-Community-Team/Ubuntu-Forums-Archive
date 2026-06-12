---
title: "Install Error - No Grub, Install on RAID disk failure"
date: 2024-02-29
forum: Installation &amp; Upgrades
---

### Post by greenmaxubx on 2024-02-29
[IMG]https://pasteboard.co/9mFL6ELGAzvl.jpg[/IMG][IMG]https://pasteboard.co/9mFL6ELGAzvl.jpg[/IMG]Hi Experts,

System: Fujitsu Primergy TX100, 8 Core 32G RAM system, RAID 1 - 1TB x 2 System
No UEFI, hence legacy
Load from USB is configured on BIOS and it does this well. 
RAID - to my understanding is Hardware RAID, as this is the first one which comes up on screen, and then BIOS option, and then when Boot Menu (Grub) should be shown, it now comes as blank.

(I am not an expert, so please bear with me if the details here are not super good)

It was running beautifully on Ubuntu 18.04. I decided to wipe clean (reformat entire disk) and re-install, where it all went south. 
Note, this system previously had windows as well, which I wanted to clean up completely. 

In summary, attempting to reset the system from scratch upwards for Ubuntu.

When the installation comes to disks section, there are already two partitions on the disk - I have configured a partition for 500M as /boot, 929 G as / and left another 1 M on the disk - as spare (just in case for grub). 
The system doesnt allow me to choose harddisk as boot device, and hence have configured the USB as the boot device
Do refer to screenshot #1 on how I have configured the disks manually now.

After this step, there is a installation error as in Screenshot#2 and #3.

Could you advice on what I might be doing wrong?

[IMG]https://pasteboard.co/9mFL6ELGAzvl.jpg[/IMG]

---

### Post by yancek on 2024-02-29
> No UEFI, hence legacy 

What does that mean?  The 3rd image you posted clearly shows partition 2 is unused esp formatted vfat??
Did you have 18.04 installed in Legacy mode?  If your hardware is newer than 10 years old, it should be UEFI capable and the drives GPT.  It would make more sense to install in UEFI mode.


Which release of Ubuntu are you trying to install, 22.04 or one of the short term releases?  Was your 18.04 install using LVM?  RAID?

Your first image as well as the 4th image contain the message "Devices or container for RAID must be specified" so you need to do that.  Never used either myself so can't help with it.

---

### Post by greenmaxubx on 2024-02-29
> **yancek said:**
> What does that mean?  The 3rd image you posted clearly shows partition 2 is unused esp formatted vfat??.

Thats the USB.
If you observe - screenshot01_.jpg - 3rd image, on how the storage is configured, thats the only one which show the option -to set as Boot Device. 
The other one - md126 - doesnt have this option to set as boot device.  
Without setting this option as boot device on one of them, I cannot proceed.  Hence, for now, just set the one which gave the option / USB with VFAT - to continue with the installation.
You can observe the USB at the bottom half of the screen.


> **yancek said:**
> Did you have 18.04 installed in Legacy mode?  If your hardware is newer than 10 years old, it should be UEFI capable and the drives GPT.  It would make more sense to install in UEFI mode. 
I didnt expect so many issues and hence didnt observe / don't know about the previous configuration.
I cannot find UEFI in the BIOS settings and hence assuming this one to be Legacy.


> **yancek said:**
> Which release of Ubuntu are you trying to install, 22.04 or one of the short term releases?  Was your 18.04 install using LVM?  RAID?
As of now was trying with 20.04 (Focal)
Not sure about the config for 18.04, The system has Hardware RAID built in, as mentioned in original info, that the RAID loads up first, and then the BIOS menu. Also, there is a menu (similar to BIOS) for RAID, where in I have done a "rebuild" for the RAID and it shows as "Online", so no issues there.
Are you suggesting I should define a LVM, if it was previously there?
**Update : **yes the previous config was with LVM< which I can see when I went through the default storage settings (and not manual configuration). I still get the error as in below comment


> **yancek said:**
> Your first image contains the message "Devices or container for RAID must be specified" so you need to do that.  Never used either myself so can't help with it
How do I mention this ? 
If you observe the Image#3 / Storage configuration - (md126) + USB (VFAT one) - are only there, while the  md127 - is RAID driven. Hence what else is to configure, I am a bit lost here.


In an ideal world, if you were to consider this as a "Fresh" system, how would I go about installing Ubuntu OS on this hardware?

---

### Post by greenmaxubx on 2024-02-29
Have tried with Ubuntu 22.04 (previous try above was with ubuntu 20.04) 
results have not changed, though the error seems to convey similar message around disk issues. 

Had to go with the default disk configurations, as with manual disk configuration, it was not allowing me to select "Use as boot device" option which was disabled / greyed out. 

attached  are the default disk configurations and error with Ubuntu 22

---

### Post by yancek on 2024-02-29
Most computers sold in the last 10+ years are UEFI capable so unless your computer is older than that, it is likely UEFI capable.  Is your drive GPT?  It would seem so from the information you posted.  I've not used RAID or LVM so can't be of any help in that area.

Your first image in post 4 shows device or resource busy in regard to sda2 but what is sda2?  Note the errors below that line refer to the subiquity installer and all the errors are resulting from the sda2 being busy.

---

