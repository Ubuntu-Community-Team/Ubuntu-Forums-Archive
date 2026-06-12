---
title: "Installing Ubuntu 11.10 on External HD"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by Sojournermiller on 2011-11-07
Hello,
 I had major issues with running Vista, and had decided to just use  Ubuntu. I still used vista for some apps that I could not get on Ubuntu,  so just ran them side-by-side. I've been doing that for about a year,  and suddenly windows started acting funny over the last week, i.e.  running slow, getting a lot of error messages, which indicated to me  that, One: I had a virus, or Two: My HD was about to tank. I have always  been pretty anal about running my clean programs, back-ups (to  externals), virus software and tweaks to make sure my system worked at  it's best, but I know sometimes even my best can't keep a bad HD from  crashing.
 So just to be safe I did a system restore back to about a month ago,  that didn't help. Then I started getting all these pop ups with for all  of my start programs telling me that they could not open. Now that  sounded like a virus, so I did all my virus scans, which of course said I  didn't have a problem. I know from past experience, that that doesn't  mean you don't have a virus. So I decided then to just wipe out my hard  drive and install Ubuntu 11.10 as my OS, seeing as windows wasn't  playing nice and I didn't care to go back to using it anyway. 
 Upon rebooting with the live CD windows did something I've never seen before, and I got this message:
 
 [ Intel UNDI, PXE-2.1 (build 082) Copyright (c) 1997-2000 Intel Corporation
 
 For Realtek RTL8101E/8102E PCI-E Ethernet Controller v1.07 (080320) 
 PXE-E61: Media test failure, check cable
 
 PXE-MOF: Exiting PXE ROM.
 No bootable Device -- insert boot disk and press any key]
 
 After rebooting again and getting the same message, I tried the F8 key  to get into Safe mode, and it would not let me do that. So I tried all  of them. The only one that would open was F2, I was able to change the  boot order and just went ahead and booted with my Windows Vista Recovery  boot disk, which did not work. Could not find my HD.
 
 So now that I've done pretty much all I can do on my own with this. I'm  asking, is it possible to run Ubuntu 11.10 from my External HD (1TB).
 
 My System Info: Toshiba Satellite L305D-S5928, AMD Turion 64 X2  Dual-Core Moblile Tech TL-62, Windows Vista 32-bit, 3GB PC6400 DDR2  800MHz SDRAM, 320GB HHD (5400rpm)
 
 Any and ALL help is very much appreciated!
 
 SojournerMiller :confused:

---

### Post by darkod on 2011-11-07
Yes, you can. Just install as normal and specify the extHDD as the destination. Also make sure you select the extHDD as destination for grub install, it's better.

If it can't see your intHDD at all, you will not have other choices for installation of the OS and grub anyway.

---

### Post by Sojournermiller on 2011-11-07
Thank you! I've decided to put it on my 160GB external I have as a spare instead of my 1TB, seeing as the 1TB is the one I back-up most of my data on, I don't want to mess with putting an OS on there and having issues later. 

Does it matter whether I partition the external or not? I will only be putting Ubuntu on it.

---

### Post by darkod on 2011-11-07
You mean whether to partition manually or let it automatically? The installation will partition the disk anyway.

I always partition manually for greater control. But it's up to you.

---

### Post by Sojournermiller on 2011-11-07
At this point I think I'm going let Ubuntu partition it, seeing as I will only be using it for Ubuntu. I was thinking about doing it manually, but I'm so ready to take this machine out back and use it for target practice. (grin)

---

### Post by Sojournermiller on 2011-11-07
> **darkod said:**
> Yes, you can. Just install as normal and specify the extHDD as the destination. Also make sure you select the extHDD as destination for grub install, it's better.

If it can't see your intHDD at all, you will not have other choices for installation of the OS and grub anyway.

Ok I had to reinstall Ubuntu to my external HD, because I got an error message saying:

couldn't read file.
Press any key to continue...

What is it NOT reading? I wasn't given an option to direct the grub install to the extHDD, so I don't know what I can do from here.

---

### Post by darkod on 2011-11-07
It would help to specify which file, if the message said that. Is it during the install or when you tried to boot the installed ubuntu?

The option to select where to install grub might appear only when doing manual partitioning. I always do manual, so I don't know for sure how it goes for the other options. But you said the intHDD is not even recognized any more, so grub has to go to the extHDD anyway. And when you select the extHDD as destination I think grub goes there automatically too.

---

### Post by Sojournermiller on 2011-11-07
> **darkod said:**
> It would help to specify which file, if the message said that. Is it during the install or when you tried to boot the installed ubuntu?

The option to select where to install grub might appear only when doing manual partitioning. I always do manual, so I don't know for sure how it goes for the other options. But you said the intHDD is not even recognized any more, so grub has to go to the extHDD anyway. And when you select the extHDD as destination I think grub goes there automatically too.

It doesn't specify what file, but right now I'm on a screen that says [GNU GRUB version 1.99-12ubuntu5, and below it gives you 4 options to choose from:
Ubuntu, with Linux 3.0.0-12generic
Ubuntu, with Linux 3.0.0-12generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest84+, serial console 115200)
[use the up arrow and down arrow to select which entry is highlighted.
Press enter to boot the selected OS, "e" to edit the commands before booting or "c" for a command-line.

I tried the first one and got a black screen and the cursor just blinking, then got a bunch of: 
-----udevd [#]: '/sbin/dodprobe -bv usb:v04B4p0060d0001dc00dp00ic03isc01ip02' [#] terminated by signal 9 (killed)

Then:
ata_id [277] : HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument

So now I'm lost.

---

### Post by darkod on 2011-11-08
Have you tried removing the failed int hdd? It might be trying to read it and throwing an error. If it's really failed no point in keeping it connected.

---

### Post by Sojournermiller on 2011-11-11
> **darkod said:**
> Have you tried removing the failed int hdd? It might be trying to read it and throwing an error. If it's really failed no point in keeping it connected.

I downloaded Hiren's boot CD and I still couldn't recover my HHD and know it's not even reading it, so I'm just going to replace it with a new one. But thanks for your help.

---

