---
title: "Dual Booting installation problems"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by n8dude on 2007-03-20
Hey guys, i'm having trouble dual-booting windows and ubuntu.
(i would just get rid of windows completely but my parents wont let me)
I can boot into the Live-cd, but when i try to install it, i run into trouble at the partitioning table.
i try to repartition the drive, but it just freezes up for a little bit, then goes back to the partitioning screen. I tried using gparted, but that gave me an error. 
System Specs:
Amd Athlon Xp 2200+ 1.8ghz
Ati X1600 Pro 512mb 
512mb ddr 400 ram
120gb hd, 30gb free
600watt psu

If any of u guys have run into similar problems, let me know, help is much appreciated.

---

### Post by chewearn on 2007-03-21
I suggest two things you can do:
1. In Windows, defrag the Windows partition a few times to make sure the files are moved to the beginning of the partition
2. Use you favorite partition utility (e.g. GParted LiveCD) to resize Windows partitionto  create a few gig of continuous unallocated space.

Then, you should be able to install ubuntu straight into the unallocated space; not need to fiddle with partition tables during installation process.

---

### Post by n8dude on 2007-03-21
i defragged about 5x, and still nothing. I want linux soooo bad, and i dont know what the heck is going on, ive never experienced problems like this before on all my dual boot installs.

---

### Post by rsambuca on 2007-03-21
I would definitely consider clearing out a bit more space on that drive.  If you are trying to divide the remaining 30 gigs between ubuntu and windows, you may have a few problems as XP likes some extra room to work with.

---

### Post by n8dude on 2007-03-21
k, ill do that, i am just so sick of windows and its...... :mad: 
i've been trying for a long time now to get ubuntu to work, i just wish i could nuke the whole windows install.
ill re-post if it works or not.

---

### Post by n8dude on 2007-03-26
still nothing. ive cleared up about 50gigs now, and still nothing. 
BTW: this pc is not from companies like hp or dell. i built it myself. so that clears up any stupid crap from dell.
if anyone has had any problems like this please post.

---

### Post by confused57 on 2007-03-26
> **n8dude said:**
> still nothing. ive cleared up about 50gigs now, and still nothing. 
BTW: this pc is not from companies like hp or dell. i built it myself. so that clears up any stupid crap from dell.
if anyone has had any problems like this please post.

May not make a difference, but you might want to try the alternate installation cd.  Did you try the gparted live cd, as AstalaVista suggested:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

