---
title: "gparted &quot;no devices detected&quot; when installing 10.10"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by ADLUX on 2011-01-08
Trying to install 10.10 to dual boot on my desktop that is running Windows 7 (64bit).  Tried 2 different disks for the install live cd.  When going into gparted everything is greyed out and showing "no devices detected".  
Went into bios for the Sabertooth X58 and found different options for storage configuration.  Currently setup as "RAID".  Have alternative options IDE or AHCI.  Tried all options and retried the installation with same results.  Not sure which configuration will help the installer detect the HD.

Tried "sudo fdisk -l" on all configurations and nothing detected.  Any suggestions?

Intel Core i7-950 3.06ghz
Asus Sabertooth X58
HDO 500GB Sata II 3G NCQ HDD

---

### Post by cascade9 on 2011-01-08
If you cant see the HDDs in IDE, SATA or RAID...I'd bet you (or whoever built the computer) used the 'SATAIII' ports (marvel 9128 controller). They have poor/no support so you cant see the HDDs.

---

### Post by ADLUX on 2011-01-08
I have a side access panel and I will see what ports they used.  If they did use them, what port should I switch it too?  By doing this should I expect any issues with the other OS?

---

### Post by cascade9 on 2011-01-08
If I'm right, you HDD will be hooked up to the white ports (only 2 of them). If yuo want a linux distro to see the HDD, it should be hooked up to the darker ports (charcoal/brown ports, 6 of them)

I wouldnt be suprised if windows freaked out over the change, or refused to boot.

---

### Post by ADLUX on 2011-01-08
Was able to partition and install fine after your recommendation.  Thanks alot for the help!

---

### Post by cascade9 on 2011-01-09
Glad it helped ;)

---

### Post by Peterpuck12 on 2012-08-31
I am also trying to install ubuntu 10.10 to my a brand new HDD (WDC WD800AAJB-00J3A0 0.103E01).  My BIOS (Award Modular, v6.0PG) for the SOYO SY-K7ADA v1.0-2AA1 recognises that my HDD does exist, but gparted has the same result that ADLUX had; it is greyed out and showing "no devices detected".   

I posted a thread previously about this situation, and in summary, I was told to just mess around with the BIOS settings with no certain direction to start to look.  Since I attempted to configure my BIOS with no previous experience with this portion of the computer, I put this project on hold until I found enough time to continue.  I am quite new to the BIOS settings area, and not sure which configuration will help the installer detect the HDD.  

Any ideas where I may be able to continue this debacle?





Motherboard: SOYO SY-K7ADA v1.0-2AA1
Main Processor: AMD Athlon 1700+
Primary Master: WDC WD800AAJB-00J3A0 0.103E01


Previous Thread: [http://ubuntuforums.org/showthread.php?t=1724963](http://ubuntuforums.org/showthread.php?t=1724963)

---

### Post by drdos2006 on 2012-09-01
I just did a repair on a friends desktop machine this afternoon which was dual-boot with Windows 7 in the primary partition, Ubuntu 12.04 in the secondary partition, NTFS as the third data partition and the fourth partition as the swap-file.

Windows would boot ( sort of ) but would hang when trying to click Ctrl-Alt-Delete to access the TaskManager.  Ubuntu would not boot with the onscreen drop down list boot manager selection.

Booted with Live CD, gparted would not see the harddisk. Switched the machine off.

So, removed all electrical cable, printer, mouse, keyboard and opened the case. 
Removed and reset ( replugged ) the SATA connections on the motherboard and the hard drive, reseated the memory, plugged all the cable back in and the machine now dual boots with everything as it should be.

regards

---

### Post by mörgæs on 2012-09-01
The thread concerns 10.10, which is an obsolete release. Therefore closing.

Peterpuck12, please try again with 12.04 and feel free to open a new thread if you still are having problems.

---

