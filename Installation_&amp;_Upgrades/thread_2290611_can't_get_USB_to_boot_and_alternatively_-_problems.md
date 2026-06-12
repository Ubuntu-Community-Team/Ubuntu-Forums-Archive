---
title: "can't get USB to boot and alternatively - problems with a CD bootable disk"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by ray28 on 2015-08-13
My first post to the forum.  There certainly seems to be lots of willing help available!
 
A senior friend has been having problems with Windows XP.  She is a light user, accessing her g-mail through Firefox and creating a small number of documents in word-processing.   Installing UBUNTU seemed like it might be a solution that would work on her older CPU and eliminate the need to purchase a new machine and of course to junk this one..
 
I had an older UBUNTU 12.04.1 LTS boot disk and the install went well but the system still seemed slow so I investigated LUBUNTU and it seemed to me that the system might perform faster on a lite version.
 
I downloaded a LUBUNTU 14.04.2 LTS iso file and tried to create a boot disk on a USB stick.  I have tried both the *Universal USB Installer* and the *LinuxLive USB Installer* without success.
 
I have set up the BIOS so that the 1[SUP]st[/SUP] bootable device is the USB-HDD.  The LED light on the stick turns on but then it goes to the hard disk and boots UBUNTU from there.  I can view the files and folders on the (not) bootable USB drive while it is inserted in the machine, so I am assuming that all should be well and if I did the rest properly it should boot and work.
 
This old machine doses not have a DVD drive on it (just a CD drive) so the LUBUNTU 14.04.2 LTS at 703 MB will not fit on a 700MB CD that I have on hand.  However, the “not for the faint of heart” LUBUNTU 15.02 version at 696MB would fit so I downloaded an iso file for it.  I tried to create a bootable CD using the Windows 7 “windows image disk burner” utility and after copying, the verification process found an error and it stopped.  Just to see what might happen I put it in the CD drive of the old machine to see if it would boot, and it did.  As one would expect the disk check utility discovered the error as well but it went ahead and attempted to install LUBUNTU anyway.  Unfortunately there were errors displayed on the screen and eventually it ended up reverting to booting UBUNTU from the hard disk.  (For the record, I downloaded the iso file a second time and tried burning it again with the same results.)
 
My preference would be to install the stable LUBUNTU 14.04.2 LTS version on the machine, but I can’t seem to find any success in creating a bootable USB for it.
 
I am wondering if the problem is with the USB port on the CPU or the USB stick itself, Given that the system can read the files on the stick I conclude this is unlikely.  Or is it the ISO file burned to the stick, or is it something else.
 
Any advice would be appreciated.  As you probably gathered I am a neophyte at this.  I am not even sure of the right question to ask, so I hope that my description above is enough to lead me to some advice and a way to create a bootable LUBUNTU USB.
 
Thanks in advance.

---

### Post by ubfan1 on 2015-08-13
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

Changing USB ports on a machine might help.  Does the USB work on another machine?

---

### Post by ray28 on 2015-08-13
Thanks for the tips.  Clearly I have some homework to do.  I'll be back as soon as I complete it.

---

