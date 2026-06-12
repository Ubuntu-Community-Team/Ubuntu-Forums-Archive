---
title: "After updating grub on wubi 10.04, my pc just won't boot to windowsXP"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by Urgenthelp on 2010-07-25
Before anything else, here's the computer's specifications:
Asus 1000he (netbook)
Intel Atom N280 1.66Ghz
2Gb of RAM

Computer description:
Dual booted for Windows XP and Windows 7

Problem:
Wubi 10.04 was working great when I first installed it on WindowsXp, even after restarting after installation. BUT after updating GRUB, which I though would not do anything bizarre, My PC showed and prompted up

ERROR: No such device: (And a bunch of numbers, after googling it. It might be the UUID)
grub>

After doing what this website said, [http://www.linux.com/community/forums?func=view&id=4219&catid=18](http://www.linux.com/community/forums?func=view&id=4219&catid=18) and [http://www.omaregan.com/?p=608](http://www.omaregan.com/?p=608) and all the instructions here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search) and reinstalling the GRUB on terminal using liveCD which failed miserably. because the terminal said that no grub was installed? so i installed it.

It booted into this:

GNU GRUB version 1.98-1ubuntu5

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

*I just want to be able to use WindowsXP again because its where I do all the work after all, I was just curious in testing ubuntu. :(
Just need to be able to boot it back to XP and win7.

PS: before i forget... since its a netbook, I boot it up using a external cd drive and I have to go into bios and let the driver load up before I could boot into any linux distro.

---

### Post by theozzlives on 2010-07-25
Why you installing WUBI??? Do a triple boot and install Ubuntu the way it's supposed to. Don't mess with GRUB, I can't say any more.

---

### Post by wilee-nilee on 2010-07-25
You have done a bit of work so post the bootscript in my signature. Paste the output to a reply highlight the txt and click on the # in the reply panel then submit reply.

This script can be run from any Linux environment, including a live cd booted. The script will not work in Windows.

---

### Post by bcbc on 2010-07-26
> **Urgenthelp said:**
> Before anything else, here's the computer's specifications:
Asus 1000he (netbook)
Intel Atom N280 1.66Ghz
2Gb of RAM

Computer description:
Dual booted for Windows XP and Windows 7

Problem:
Wubi 10.04 was working great when I first installed it on WindowsXp, even after restarting after installation. BUT after updating GRUB, which I though would not do anything bizarre, My PC showed and prompted up

ERROR: No such device: (And a bunch of numbers, after googling it. It might be the UUID)
grub>

After doing what this website said, [http://www.linux.com/community/forums?func=view&id=4219&catid=18](http://www.linux.com/community/forums?func=view&id=4219&catid=18) and [http://www.omaregan.com/?p=608](http://www.omaregan.com/?p=608) and all the instructions here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search) and reinstalling the GRUB on terminal using liveCD which failed miserably. because the terminal said that no grub was installed? so i installed it.

It booted into this:

GNU GRUB version 1.98-1ubuntu5

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

*I just want to be able to use WindowsXP again because its where I do all the work after all, I was just curious in testing ubuntu. :(
Just need to be able to boot it back to XP and win7.

PS: before i forget... since its a netbook, I boot it up using a external cd drive and I have to go into bios and let the driver load up before I could boot into any linux distro.

You need to get the windows boot loader back in place. It seems a recent grub-update is installing the grub bootloader on wubi installs, and this (as you can see) breaks both windows and wubi.

So, your choices are, insert a windows repair cd and replace the bootloader, or, install the lilo bootloader (to achieve the same result).

To install lilo, you'll need to boot from the live CD and enter:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

It will still help to post the bootinfoscript results if you want a definitive answer. e.g. if you have more than one drive and you are booting off the second (less typical but it happens).

Please can you also post back if you recall a grub screen during the updates that asked you to select all drives to install grub (it would have been very noticeable and you would have had to click on some checkboxes like [] /dev/sda) - this will help us figure out what is wrong with grub and hopefully get this bug fixed quicker. Thanks

---

### Post by Urgenthelp on 2010-07-27
i initially thought i only had three partition drives. :|
here my booting partition based on the boot info.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63  sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 =  8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O  size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd65316e1

   Device Boot      Start          End      Blocks   Id  System
/dev/sda1               2       10659     85610385    f  W95 Ext'd (LBA)
/dev/sda2    *       10660       18814    65505037+   7  HPFS/NTFS
/dev/sda3           18815       19452     5124735   1c  Hidden W95 FAT32  (LBA)
/dev/sda4           19453       19457       40162+  ef  EFI  (FAT-12/16/32)
/dev/sda5               2       10659    85610353+    7  HPFS/NTFS
```I can't recall the grub message... wah?
I don't remember checking a [] of some sort...
But I remember the prompt that came with updating, maybe I randomly pressed?
I'm trying out the lilo fix since that windows cd fix couldn't work because I remember not placing a password for XP. I made it automatically login. But during standbys by password's just blank.
Hoping it works.

Thanks to all your replies, I really appreciate the effort.

---

### Post by Urgenthelp on 2010-07-27
> **bcbc said:**
> You need to get the windows boot loader back in place. It seems a recent grub-update is installing the grub bootloader on wubi installs, and this (as you can see) breaks both windows and wubi.

So, your choices are, insert a windows repair cd and replace the bootloader, or, install the lilo bootloader (to achieve the same result).

To install lilo, you'll need to boot from the live CD and enter:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```It will still help to post the bootinfoscript results if you want a definitive answer. e.g. if you have more than one drive and you are booting off the second (less typical but it happens).

Please can you also post back if you recall a grub screen during the updates that asked you to select all drives to install grub (it would have been very noticeable and you would have had to click on some checkboxes like [] /dev/sda) - this will help us figure out what is wrong with grub and hopefully get this bug fixed quicker. Thanks

YOUR A LIFESAVER, MAN!
The Lilo trick worked flawlessly! :DDDDD
I'm so happy. :)))
Now off to figure out how to partition ubuntu separately to make a triple boot.
I could ask for some pointers on reworking the partition table.

THANK YOU!

---

