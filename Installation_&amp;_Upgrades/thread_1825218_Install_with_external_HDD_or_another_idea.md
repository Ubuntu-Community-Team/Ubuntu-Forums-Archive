---
title: "Install with external HDD or another idea?"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by dwigyit on 2011-08-14
Hello - my auntie's HP laptop is years old, runs Windows Vista and hasn't been reinstalled, ever. It's full of bloatware and random programs that I have no idea how they got there, no doubt a good few are viruses.

Anyway, I want to install Ubuntu on it, but have a small problem. The CD drive doesn't really want to load Ubuntu from a CD, though I'm not surprised considering its age - it probably doesn't work at all. Also, my normal Ubuntu USB stick, which uses USB 2 high speed, doesn't seem to work on the laptop, not even within Windows (gives unrecognised device error) and so I can't boot from it. We're looking for an older (USB 1 maybe?) memory stick in the house but doubt we'll be able to find one.

The one device which does work, however, is my WD external hard disk drive. The Ubuntu live CD creator wont install to it, of course, but if there was a way to use it to install ubuntu, that would be great.

Thanks in advance ;)

---

### Post by varunendra on 2011-08-15
First off, if it supports Vista, it must definitely have support for USB2. Is the USB key able to boot other computers? Is it detected in BIOS? Is there a BIOS setting that says something like "Legacy USB...." and is enabled?

Secondly, AFAIK, all USB2 storage devices are backward compatible to USB1, so you shouldn't have problem getting them detected in a USB1-only computer. But as I said above, I'm sure the laptop must have USB2 support.

Now on to a solution, hopefully a guaranteed one:-

You can make an external hard drive a Live USB without problems. I've done it with my portable 320GB Seagate and a portable 500GB SiliconPower drive. All you need is a FAT32 partition (preferably a primary one) on the drive. This partition should be detected as a possible destination for installation by the USB creator.

Now how you create such a FAT32 partition on it and how you make it live depends upon the resources you have. I used a Live CD to do so. A virtual machine can also do it for you as follows:

[LIST=1]
[*]boot the VM with the downloaded iso
[*]attach the external drive to the VM
[*]run gparted and resize the first partition of the external drive sliding it to its right to get space for the new FAT32 partition
[*]create a new FAT32 partition in the space
[*]run startup disk creator, and choose the FAT32 partition as the destination.
[*]detach the hard drive and reboot the laptop.
[*]choose your external drive as boot device and it should boot just like any Live USB.
[/LIST]
I'd be glad to assist if you need help doing this.

---

### Post by YesWeCan on 2011-08-15
This looks promising: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[Sorry, I keep editing my post because I find something that looks usable like network installation but on further reading it is unusable from Windows.]

---

### Post by dwigyit on 2011-08-15
Woops - I accidentally pressed erase disk on the FAT32 partition thinking it would format only that partition. Instead it wiped my entire backup drive. Ah well, stuff happens :D

Anyway yeah I had already tried making a FAT 32 partition, but didn't know that the live USB creator would treat it any differently to an NTFS one so I hadn't thought to re-run it - had just copied over the files from my ubuntu USB, it didn't work as you can imagine. Thank you for the advice - I'll give the proper method a try now (using my entire 500GB drive, it would seem lol :( )

---

### Post by dwigyit on 2011-08-16
Works perfectly, thank you :)

Will mark thread as solved now ;)

---

