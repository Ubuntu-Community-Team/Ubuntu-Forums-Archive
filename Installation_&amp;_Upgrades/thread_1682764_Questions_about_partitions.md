---
title: "Questions about partitions"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by MelodiesonMusic on 2011-02-06
Right now, i'm using Ubuntu 10.04. When i first installed it i was planning to do a dual boot between the windows XP that i had and the Ubuntu that i was installing. Unfortunately i had no clue what i was doing and deleted windows... now all i have is Ubuntu. I don't want to go back to windows permanently but i do want a minimal install so that i can play a few games i can't play under wine. When I run the XP setup I have two partitions. One with about 90000 MB and the other with about 3000 MB, they're both unrecognized. I need to know which one has Ubuntu on it, and why the other isn't already empty. Is there anyway i can boot up the other partition to see what's going on in it?

---

### Post by mikewhatever on 2011-02-06
The bigger partition is likely to be the Ubuntu one, while the other is probably the swap partition. To install XP, you'll need to resize the Ubuntu partition with Gparted, running from the Ubuntu live cd. After that, the Windows installer should recognize the unallocated space and be able to install XP there.

---

### Post by MelodiesonMusic on 2011-02-06
wow, that was speedy :p Soo, if i use this GParted program, how much space do you think i'll need for a minimal install of windows? And how exactly do I use it while booting from the live CD? :confused:

---

### Post by jroa on 2011-02-06
Before you do anything else, you probably want to make sure that Windows did in fact get deleted.  Open a terminal and enter the following.

sudo fdisk -l

This will show all of your partitions.  Then, copy and paste back here and we should be able to tell you if one of those partitions is probably your Windows.

---

### Post by MelodiesonMusic on 2011-02-06
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11716    94108738+  83  Linux
/dev/sda2           11717       12161     3574462+   5  Extended
/dev/sda5           11717       12161     3574431   82  Linux swap / Solaris

```

---

### Post by jroa on 2011-02-06
Yep, you lost Windows.  You can use GParted with the live cd to create a new partition.  The size depends on the Windows distro.  If it is XP, then I think you can get away with only 10 - 20GB, but if it is Vista or 7, then I would have to do some research to find out what the minimum recommended size is.

---

### Post by MelodiesonMusic on 2011-02-06
Oh thanks :) so about this whole live cd thing.. I just dig out the cd i used to install, select the trial thing instead of the install, get GParted and run it from there?

---

### Post by jroa on 2011-02-06
Yes, that is pretty much it.  I don't know what version you are using, but GParted may or may not be included.  If it is not, you can install it once you are logged in to the live disk.

Edit to say that you can download a GParted live iso and burn that to a cd too.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by MelodiesonMusic on 2011-02-06
Yay :) Thanks for the help

---

### Post by dino99 on 2011-02-06
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by kansasnoob on 2011-02-06
> **jroa said:**
> Before you do anything else, you probably want to make sure that Windows did in fact get deleted.  Open a terminal and enter the following.

sudo fdisk -l

This will show all of your partitions.  Then, copy and paste back here and we should be able to tell you if one of those partitions is probably your Windows.

+1!

BTW that's a lower case L at the end.

This general guide still works with XP, **[COLOR="Red"]but everything about grub is wrong![/COLOR]** So ignore everything it says about the bootloader/grub!

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Once the installation is complete, and you know XP is booting OK, you need to boot the Ubuntu Live CD and follow the **How to restore the Ubuntu grub bootloader (9.10 and beyond)** section of this guide:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you're at all in doubt regarding device designations or such please just post the output of this command and we'll help you:

```
sudo fdisk -l
```

BTW that's a lower case L at the end.

---

### Post by srs5694 on 2011-02-06
> **jroa said:**
> Yep, you lost Windows.  You can use GParted with the live cd to create a new partition.  The size depends on the Windows distro.  If it is XP, then I think you can get away with only 10 - 20GB, but if it is Vista or 7, then I would have to do some research to find out what the minimum recommended size is.

Don't forget to include the size of the software you want to run under Windows; that size requirement could add significantly to the disk space needs.

Also, be aware that the recovery/installation discs that come with some computers are very aggressive about using disk space; they might not give the option of preserving the Linux installation. It sounds from the description posted earlier like the installer being used is not one of the really obnoxious ones, but I thought it worth mentioning, particularly in case somebody else with the same problem reads this thread in the future.

---

### Post by kansasnoob on 2011-02-06
> **srs5694 said:**
> Don't forget to include the size of the software you want to run under Windows; that size requirement could add significantly to the disk space needs.

Also, be aware that the recovery/installation discs that come with some computers are very aggressive about using disk space; they might not give the option of preserving the Linux installation. It sounds from the description posted earlier like the installer being used is not one of the really obnoxious ones, but I thought it worth mentioning, particularly in case somebody else with the same problem reads this thread in the future.

+1 regarding all of that!

I've not seen it much with XP, but somewhat with Vista, and a lot with Win7 where "branded OEM discs" will absolutely restore the box/book/lappy to original state only, or at least insist on creating the original number of partitions.

I still remember when it took three discs to restore an HP branded Win ME :p

---

### Post by mikewhatever on 2011-02-06
One other thing to mention, that I think no one has yet, after you are done reinstalling Windows, there won't be any option to boot Ubuntu, just Windows. That problem is easily taken care of by reinstalling grub from the live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

