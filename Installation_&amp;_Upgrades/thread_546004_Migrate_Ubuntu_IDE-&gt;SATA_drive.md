---
title: "Migrate Ubuntu IDE-&gt;SATA drive ?"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by Beowulf.1000 on 2007-09-08
I want to migrate Ubuntu from the current IDE drive it is on to a SATA drive. Currently I have WinXP on hda (ide0) and Ubuntu 7.04 on hdb (ide1), and several sata drives for data, etc.   This past week I installed WinXP and Ubuntu 7.04 to a friend's PC (including nvidia drivers and Beryl, he is quite impressed with linux now!), to sata1 and sata2 respectively.  The sata drives are lightning fast (3GigaBytes/sec) so I also want that speed and also storage (400G B drives).

I guess I will wait for 7.10 that should come out in a few weeks. But what is the best strategy to do a migration without losing all my settings, etc? Or should I just do a fresh install to sata after first backing up all my data to external USB drive(s)?

BTW, the install of WinXP and Ubuntu 7.04 to (my friend's PC) the sata drives was interesting/frustrating. Googling shows it to be a nightmare because Grub has major problems doing this. WinXP went to sata1, then Ubuntu live CD install to sata2, but near the end of the ubuntu install grub wanted to install to "(hd0)".  Only the DVD-CD drive (hda), and the two sata drives were connected.  The problem is grub wanted to install I think to the DVD-CD drive, which is not possible, and the install of grub fails. So I edited Ubuntu's default of (hd0) and changed that when asked to (hd1) and the install of Ubuntu 7.04 to the sata drive with grub onto sata1 (WinXP) worked fine.  Nice dual boot system now.

---

### Post by logos34 on 2007-09-08
If you're currently running edgy I'd do a fresh install.  You can only upgrade one release at a time, so it would be a two-step process, edgy-->feisty-->gutsy.  Personally I plan to try the upgrade route for once...I have a separate /home, so if it borks the system then I'll just do the install.

---

### Post by Pumalite on 2007-09-08
Ditto.

---

### Post by Beowulf.1000 on 2007-09-08
I am running Feisty Fawn (7.04); I actually did the upgrade from v6 on a couple of machines and it went quite well, very impressive.  But yeah probably  best to to a clean install of 7.10 in October. I am downloading the alpha5 of 7.10 to just try out the live CD.

> **logos34 said:**
> If you're currently running edgy I'd do a fresh install.  You can only upgrade one release at a time, so it would be a two-step process, edgy-->feisty-->gutsy.  Personally I plan to try the upgrade route for once...I have a separate /home, so if it borks the system then I'll just do the install.

---

