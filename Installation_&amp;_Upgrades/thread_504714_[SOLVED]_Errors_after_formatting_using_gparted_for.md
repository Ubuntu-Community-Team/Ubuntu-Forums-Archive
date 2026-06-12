---
title: "[SOLVED] Errors after formatting using gparted for a few Ubuntu 7.04 installation"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Chunen on 2007-07-19
Hello,

I reformatted an unstable Ubuntu 7.04 installation running on a [COLOR="Blue"][(http://h10025.www1.hp.com/ewfrf/wc/product?product=3245534&lc=en&cc=us&dlc=en&lang=en&cc=us)"]HP Slimline s7620n]("[http://h10025.www1.hp.com/ewfrf/wc/product?product=3245534&lc=en&cc=us&dlc=en&lang=en&cc=us)[/COLOR]
I used a Gparted CD to delete old partitions and create one new ext2 partition.

After rebooting to the Ubuntu 7.04 CD, the system hangs about 2 seconds after displaying the GNOME splash screen.

I have tried the following options:
[LIST=1]
[*]Started in Option 1 (Start or Install Ubuntu) as well as Option 2 (Safe graphics mode)
[*]Used a standard 1280x1024 LCD as well as a 1440x900 Widescreen LCD.
[*]Tried Xubuntu 7.04 CD as well as Kubuntu 7.04 CD.
[/LIST]

I would appreciate your help in getting a solution.

---

### Post by jim_p on 2007-07-19
Have you tried using the alternate installation cd?

It may be a failed recording on the medium, but with 3 different distros, it seems weird.

Also make sure you burn your disks on a sloooow speed and 
always check the md5sum of the .iso file you downloaded.

---

### Post by dabl on 2007-07-19
> **Chunen said:**
> 
I reformatted an unstable Ubuntu 7.04 installation 

I kinda hate to ask, but is it possible that the instability is in the hard drive itself, rather than the OS? :(

---

### Post by avik on 2007-07-19
> **dabl said:**
> I kinda hate to ask, but is it possible that the instability is in the hard drive itself, rather than the OS? :(

That would make sense, as I had similar problems with a faulty hard drive.  Removing the hard drive and using another one worked like a charm.

---

### Post by Chunen on 2007-07-20
Thanks. It turned out to be a faulty drive.
It is surprising that the boot process did start.

---

