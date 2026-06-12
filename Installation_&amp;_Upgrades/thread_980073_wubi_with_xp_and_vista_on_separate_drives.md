---
title: "wubi with xp and vista on separate drives"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by Dazed_75 on 2008-11-12
Machine (not mine) has XP on IDE0 and vista on IDE1.  When vista was added it changed the MBR on IDE0 to use the new vista boot manager which is on IDE1.  When you boot vista it calls the IDE1 drive C: but if you boot XP, the drive on IDE0 is called C:.  A wubi install requires you to specify the destination drive in Windows terms (drive letter) so normally one would specify C: for either.  However, one would also think you could specify D: since both are NTFS formatted.

Questions:

1) If one does a wubi install of ubuntu 8.10 on XP, can wubi know (and be allowed) to make appropriate changes to the vista boot manager's BCData since boot.ini is no longer used (the windows boot menu entries are now in the vista Boot Configuration Database)?  Or would wubi make its changes to boot.ini where they are probably ignored?

2) If one does the wubi install in vista, will wubi know that the C: reference needs to be considered as /dev/hdb for setup or does it not matter?  Again, will wubi update the BCD database for the vista boot manager's boot menu?

3) In either case, can one actually have wubi install ubuntu to a virtual drive file which xp/vista considers to be the D: drive and expect it to work?

I hesitate to experiment as my first attempt (maybe due to my error) caused me to have to repair XP using the XP install disk and then repair the MBR using the vista install disk.

---

### Post by Mark Phelps on 2008-11-12
They're not BOTH C: at the same time; only the OS volume is labeled as C: when that OS is running.  The other volume is probably labeled as D:.  You'll be running Ubuntu INSIDE Vista, so you need to install to the Vista volume.

---

### Post by Dazed_75 on 2008-11-12
Exactly as I stated in the original post.  Sorry, but that was not one of the questions.  I do appreciate the response but the questions about what wubi can do in an environment where boot.ini is not in use due to vista modifyiing the boot process remain open.

---

### Post by Mark Phelps on 2008-11-18
Sorry, must have misread your original post...

Since no-one has responded in five days, suggest you post this question to the wubi subforum -- perhaps someone there will help.

---

