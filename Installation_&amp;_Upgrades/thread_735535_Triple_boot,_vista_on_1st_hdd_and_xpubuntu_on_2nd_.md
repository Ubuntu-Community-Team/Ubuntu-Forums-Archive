---
title: "Triple boot, vista on 1st hdd and xp/ubuntu on 2nd hdd"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by matt1eg on 2008-03-25
Hi.

I have currently got vista installed on 1 sata hard drive on a single partition. Although i like this ive found that i need xp to run some older programs, aswell as this i want to try Ubuntu out as i have not really played with linux and am interested to try. 

I would like to install xp and Ubuntu on my second 150gb sata drive and leave vista on the first, saving me reinstalling everything on vista and setting it up again ( i have it just how i like it).

Is this possible to do? If so how? I am new to multi-booting so step by step would be great.

If having vista installed first will cause problems i was wondering if it possible to make a ghost image of that drive and then use that after i have xp and Ubuntu installed or will this not work???

Any help would be much appreciated.

If needed this is my spec

amd athlon 64 x2 6000+
2gb corsair ram
150gb sata (vista)
150gb sata (blank)
250gb ide (personal data)
8800gt 512mb
Asus M2N32 SLI Deluxe WiFi Nforce 590 Mobo

Thanks again

---

### Post by dstew on 2008-03-25
You should be able to install XP and Ubuntu on the second hard drive. Personally, what I would do would be to boot an Ubuntu Live CD, and use the gnome partition editor to partition the second hard drive before trying to install, creating a partition for XP, for Ubuntu's root file system, and for swap. You do not need to format them. Then, install XP first, and direct it to the partition you prepared for it. Then, install Ubuntu. The XP install will format its partition, and you will direct the Ubuntu installer to format the root parition and swap partition. At the end of the Ubuntu installation, install the grub boot loader into the Master Boot Record (MBR) of the first disk, and you should be able to boot Vista, XP, or Ubuntu from the grub menu.

---

### Post by matt1eg on 2008-03-30
Thanks for your help.
Tried the live cd but when it tries to load into ubuntu my monitor turns off, doesnt seem to support my graphics card. Will look for solution to that first and then have another go

---

### Post by dstew on 2008-03-30
Try booting in Safe Graphics mode. You can get that mode I think by pressing F6 at the initial Live CD screen, then choosing that option. If that doesn't work, try installing from the Alternate Install CD instead. It installs the same Ubuntu desktop system using a text based installer that works better. You get the .iso from the [Ubuntu Download page]("http://www.ubuntu.com/getubuntu/download"), just check the box below the Start Download button.

---

