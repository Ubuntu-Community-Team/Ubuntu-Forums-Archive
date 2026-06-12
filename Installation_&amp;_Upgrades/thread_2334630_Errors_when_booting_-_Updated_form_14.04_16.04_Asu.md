---
title: "Errors when booting - Updated form 14.04 16.04 Asus Ultrabook"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by mfernand2 on 2016-08-21
Hello.
Am a Linux novice. Performed an on-line update from 14.04 to 16.04 on my laptop which is an Asus Ultrabook. It has an 1T SSD and is dual-boot with Windows 8.1 via grub. Have done the same upgrade on my Intel i7 desktop without issue. It however DOES NOT have an SSD.

During boot, there are errors reported that I cannot decipher and, I believe, has to do with Ubuntu recognizing my SSD (sd9?). It is a Corsair SSD. During boot it performs some sort of disk diag that runs for 1m 50s? Sometimes it won't boot at all and I have to do the three-finger-salute (control-alt-delete).

Have a copy of my dmsg file and have attached it... (after I looked up where to find it)

Again. It's an Asus Ultrabook S500CA w/ 12G of memory (8+4 G - limitation of hardware/motherboard?). Intel® Core&#8482; i7-3517U CPU @ 1.90GHz × 4 Intel® Ivybridge Mobile w/ 11.6 GiB available for OS use... no graphics card; just Intel Graphics drivers using processor.

Not sure what to do or how to fix it... since I cannot decipher the errors.

Thanks. Appreciate the help.
Manny

---

### Post by Bucky Ball on 2016-08-21
> **mfernand2 said:**
> It however DOES NOT have an SSD.

During boot, there are errors reported that I cannot decipher and, I believe, has to do with Ubuntu recognizing my SSD (sd9?). It is a Corsair SSD.

Welcome.

??? You do or you don't have an SSD? If the SSD is not in the box, I suggest you unplug all USB dongles, drives and other devices plugged into the machine prior to upgrading. 

sd9, BTW, makes no sense as unknown syntax. It should be something like sda9 or sdd9 or something. In either case, if it's ending with a number, it is not a drive, it's a partition on a drive. sda is drive 1. sdb drive 2. sdc1 would be drive 3, partition 1.

sda9 is the first drive, partition nine.

---

### Post by mfernand2 on 2016-08-22
Let me research and will come back with an answer.

---

### Post by mfernand2 on 2016-08-22
Hi. The drive designation is sda; the partition is #9, so it's sda9. It is my root partition for Ubuntu (determined via gparted).

Again, I have Windows 7 Premium also installed on sda. I will see what I can pull from the file that sort of matches the console errors I see during boot and try to post it/them here. It is a as-best-as-I-can-recall situation since I depend on the demsg file to contain the info and what is displayed on the screen during boot does not match exactly what I see in the demsg file.

I will also see if I can capture what appears to be some disk diag that runs during boot. I do not think it is a chkdsk function but am not sure...

More info to come.

---

### Post by oldfred on 2016-08-22
Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

You show you are booting with 14.04 still?

       
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

