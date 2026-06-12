---
title: "Reboot and Select properBoot device"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by aetbanan on 2011-09-22
I have been dual booting Ubuntu 10.04 and Windows XP for a while, but using almost always XP.. then when I was installing some stupid crack the system crashed and I had to follow some guide to hack the boot sequence to get back again.

Now I decided to clean the disk and install a fresh version of Ubuntu 10.04. But after the installation I can't get further than "Reboot and Select proper Boot device". I have tried to install on both the internal disks (200 GB IDE and 500 GB SATA), with the following partitioning: 2 GB SWAP, 100 GB /, the rest /home

I have a feeling that some of the disks is ill.. it takes a long time just to get past the initial start-up when I power up the computer..


Grateful for advice!

---

### Post by varunendra on 2011-09-22
> **aetbanan said:**
> after the installation I can't get further than "Reboot and Select proper Boot device". I have tried to install on both the internal disks (200 GB IDE and 500 GB SATA), with the following partitioning: 2 GB SWAP, 100 GB /, the rest /home

I have a feeling that some of the disks is ill.. it takes a long time just to get past the initial start-up when I power up the computer..
In case of doubts about a drive's health, I would start with unplugging the IDE one first. Another thing to check initially is: proper boot sequence in BIOS and a "boot" flag on the correct drive. You can check the boot flag using gparted in Live session. Then make sure the drive with boot flag is first in the boot sequence.

---

### Post by Mark Phelps on 2011-09-22
> **aetbanan said:**
> I have a feeling that some of the disks is ill.. it takes a long time just to get past the initial start-up when I power up the computer..

Would go into the BIOS settings and change them so you get POST (Power On Self Test) messages during boot.  This will allow you to monitor the progress of the boot process.

Also, if your drive supports S.M.A.R.T monitoring, and that can be enabled in the BIOS, then do that.  Modern BIOS settings generally include something like a Hardware Health page where you can look at the S.M.A.R.T drive info.

---

### Post by Paddy Landau on 2011-09-22
Incidentally, 100Gb for / is way too much. You will be very unlikely to use more than 8Gb, so even 16Gb would be overkill. Rather put the excess hard drive into your /home partition.

---

### Post by varunendra on 2011-09-22
> **Paddy Landau said:**
> Incidentally, 100Gb for / is way too much. You will be very unlikely to use more than 8Gb, so even 16Gb would be overkill. Rather put the excess hard drive into your /home partition.
+1 to above, I overlooked that! :)

However, my preference is:
20-40 GB **/** *(including home)*
2 GB **swap**
rest **/data** *(ntfs, if the system is a dualboot with windows, or ext4 if linux-only)*

---

### Post by Paddy Landau on 2011-09-22
> **varunendra said:**
> However, my preference is:
20-40 GB **/** *(including home)*
2 GB **swap**
rest **/data** *(ntfs, if the system is a dualboot with windows, or ext4 if linux-only)*
I would still use a separate partition for [FONT=Fixedsys]/home[/FONT], so that you can reinstall or install new versions without having to restore [FONT=Fixedsys]/home[/FONT]. (But make a backup anyway, just in case.)

---

### Post by aetbanan on 2011-09-23
Thanks for the answers!

> **varunendra said:**
> In case of doubts about a drive's health, I would start with unplugging the IDE one first. Another thing to check initially is: proper boot sequence in BIOS and a "boot" flag on the correct drive. You can check the boot flag using gparted in Live session. Then make sure the drive with boot flag is first in the boot sequence.

The IDE-connected disk has the boot flag, and it is also the first in the boot sequence. I found that it was set as slave, but changing it to master didn't solve the problem..

[QUOTE=Paddy Landau]         Incidentally, 100Gb for / is way too much. You will be very unlikely  to use more than 8Gb, so even 16Gb would be overkill. Rather put the  excess hard drive into your /home partition.     .[/QUOTE]

Nice, I was hoping for comments like this as well!

[QUOTE=Mark Phelps]Would go into the BIOS settings and change them so you get POST (Power  On Self Test) messages during boot.  This will allow you to monitor the  progress of the boot process.

Also, if your drive supports S.M.A.R.T monitoring, and that can be  enabled in the BIOS, then do that.  Modern BIOS settings generally  include something like a Hardware Health page where you can look at the  S.M.A.R.T drive info.[/QUOTE]

The IDE disk is recognized as Primary Master, the SATA as SATA1 (cd as SATA2). S.M.A.R.T. is enabled (can't remember now exacly what is says about it).. Anything else I should look for?

---

### Post by aetbanan on 2011-09-27
> **varunendra said:**
> In case of doubts about a drive's health, I would start with unplugging the IDE one first. Another thing to check initially is: proper boot sequence in BIOS and a "boot" flag on the correct drive. You can check the boot flag using gparted in Live session. Then make sure the drive with boot flag is first in the boot sequence.

I disconnected the IDE drive and then I was able to install and boot without problems, and when in the system I connected it again and mounted it. I still don't know what was the problem but everything is working fine now!

How can I mark this thread as solved?

---

### Post by Paddy Landau on 2011-09-27
Glad it's solved.

> **aetbanan said:**
> How can I mark this thread as solved?
[How to mark a thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

