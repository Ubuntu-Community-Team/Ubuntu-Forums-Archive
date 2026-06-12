---
title: "Cloning"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by eeboy on 2008-04-18
I am getting ready to create a dual boot Ubuntu/XP drive on a brand new 320 GB SATA drive. I want to clone an existing XP partition from the existing 90 GB drive onto the new drive and then proceed with the Ubuntu install. Are there any cloning tools available on the live CD which will make this an easy process? 

I've tried some freeware options like XXclone (windows app) and it seems to do the job but the drive just will not boot when I substitute it in (single drive system T60p laptop). 

Any suggestions?

---

### Post by ACMarina on 2008-04-18
You'll probably need to reinstall the MBR in Windows.  The clone software doesn't really do that part, as it's hidden in the drive..

---

### Post by eeboy on 2008-04-18
Ok... how can I accomplish that? I believe the utility to perform that is fdisk mbr which is available using the recovery console (XP discs). I don't thave XP discs and I don't even have Thinkpad recovery disks.

Any thoughts?

---

### Post by Pumalite on 2008-04-18
Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by eeboy on 2008-04-19
Thanks!

I am unclear of what I am to do with SuperGrub though. Are you suggesting I take my new drive (which has the XP clone which won't boot) and install Ubuntu onto it then use SuperGrub to fix the XP MBR?

---

### Post by Pumalite on 2008-04-19
'I believe the utility to perform that is fdisk mbr which is available using the recovery console (XP discs). I don't thave XP discs and I don't even have Thinkpad recovery disks.'

Boot Super Grub and fix your MBR. Super Grub can boot any OS in your system too.

---

