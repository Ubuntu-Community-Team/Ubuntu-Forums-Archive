---
title: "Cant install ubuntu 11.10 on my HP DV2"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by hckim021983 on 2011-12-23
i have an hp dv 2, i put ubuntu 11.10 on a flash drive to boot from the drive. 
The laptop had windows xp or vista, i cant remember, and i was getting a bootmgr missing error. So i figured that i would just install ubuntu and get rid of windows. but during install i got an error message:
1)input/output error during read on /dev/sda 

so the next step i took was to just run ubuntu from the usb, it stays on the boot up screen forever!


is there a better way to approach this?

thank you so very much in advacnce for any help!!!

---

### Post by Mahkoe on 2011-12-23
I've had bad experiences with 11.10 up 'til now. I would suggest getting a different liveCD (such as gparted, [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)) and trying to figure out whether it's because your file system is corrupted, or whether your disk is busted. Try creating a new partition table, and if there are errors, I would look into getting a new hard drive/computer.

---

### Post by bobsageek on 2011-12-23
Well /dev/sda is generally your primary hard drive, so it's likely that the error you got in Windows was from a failing drive. If you are booting from the USB key into a live image it's probably doing hardware detection and getting hung up on the bad hard drive. 

If you want a lazy solution and you don't mind opening the computer, temporarily disconnect the hard drive (I think it's user accessible from a door on the bottom) and see if the live image will boot. Otherwise, the suggestion about GParted would be the more thorough thing to do.

---

### Post by Bucky Ball on 2011-12-23
Personally I'd start with 10.04 LTS, stable and reliable, that would give a better idea as 11.10 is problematic. If all good with 10.04 LTS then install a newer release on another partition (you will get the option to select either, along with Windows).

When you 'Try Ubuntu' from the 11.10 install CD does everything work okay?

---

### Post by spcwingo on 2011-12-24
I hate to be the bearer of bad news but, if you're getting I/O errors while trying to install from USB it could be that there is something wrong with either your USB flash, HDD, or even worse, the motherboard of the machine.

---

### Post by bobsageek on 2011-12-26
I'm going to disagree with all the assessments saying go back to an older version, I've installed 11.10 across a lot of hardware and it's more compatible than any prior version. Let's stay focused on what is likely a dead/dying primary hard drive.

---

