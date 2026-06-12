---
title: "boot error"
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by Theo van Nee on 2006-05-06
Hello members,
My first try at Ubuntu was to make a dual boot system with Windows. However, after installation, the bootloader gave an error 21 and I couldn't reboot my computer at all.
Then I decided to forget about Windows (kiss the blue screen goodbye) and do a new install of Ubuntu over Windows. It works fine now, but can anybody tell me what I did wrong to get this error 21, when trying to install te dual boot system?
Thanks for helping,
Theo van Nee

---

### Post by Sef on 2006-05-06
What kind of computer do you have?

This is a definition of a boot 21 error:

> Error 21 means :
"
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system.

[https://launchpad.net/distros/ubuntu/+source/grub/+bug/8978]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8978")

Click the link and read through the posts above and see if one of the solutions that people have written applies to you.

---

### Post by Theo van Nee on 2006-05-07
I have a fairly old computer. Unfortunately I cannot give the exact data, because for Ubuntu's Device Manager the processor is unknown.
From Window rememberance it is a Pentium 3, 500MHz (I think).
Disk data according to Ubuntu:
12,13 GiB, type: ST313032A
18,65 GiB, type: WDC WD200EB-00CSFO
CD drives:
CD-ROM 52X/AKH
ZIPCD 4x650

---

### Post by Theo van Nee on 2006-05-08
Got some extra system info:
Processortype: x86 Family 6 Model 7 Stepping 3
Memory: 320 MB
Class: IDE ATA/ATAPI-controllers
Device Intel(r) 82371AB/EB PCI Bus Master IDE Controller

---

### Post by Sef on 2006-05-08
Since you got it fine now, the problem seems to have been with your Windows partition.  Once you deleted it and installed an new partition, the problem was gone.  I would guess that you had Windows 98, and it had some problems due to a bad partition.

---

### Post by Theo van Nee on 2006-05-09
I had Windows XP installed. But of course the boot section might have been faulty.
Maybe if I have some spare time in the near future I might go over the whole proces again: first install Windows XP en try to install Ubuntu as 2nd OS. I would like to compare the 2 OSses. Also if it works on my PC I might suggest it to friends to promote Ubuntu.
Do you have any further tips? Or do you think I should rather install the 2 OSses on seperate disks?
Regards.

---

### Post by Sef on 2006-05-10
> Or do you think I should rather install the 2 OSses on seperate disks?
Regards.

If you installed them on separate discs, I doubt that you would see an error 21 come up.

---

### Post by Theo van Nee on 2006-07-05
Hello again,
Did a second installation:
1. I formatted disk 1.
2. Installed Windows XP on it.
3. Installed Ubuntu Breezy Badger on disk 2 and the GRUB boot loader in the boot section of disk 1.
Unfortunately I got GRUB error 21 again.
Decided to forget about Windows and write Ubuntu over it, which worked of course.
How do I get around this error 21?

---

