---
title: "Ubuntu Partitioned Disk Installation Problem?"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by gr3y5t0ne on 2008-09-05
Hi everybody,

Sorry about this, but I'm having trouble dual-boot installing Ubuntu Hardy Heron onto my desktop. I have also installed Hardy on my laptop, and that went fine.

The installation went fine until I reached the 'Partitoner' section of the installer. On my laptop installation, I had the choice to choose how much space I gave to each of my operating systems. I think it might be because my hard disk was pre-partitioned when it was running just Windows XP ( It was a 500GB disk, RAID 0 Stripe ). 

Anyway, this is the choice that I have:

Guided:

SCSI3 (0,0,0) (sda) -250.1 GB ATA WDC WD2500JS-60N

SCSI4 (0,0,0) (sda) -250.1 GB ATA WDC WD2500JS-60N

Manual


Please help me fix this problem! 

Thanks so much,

Gr3y5t0ne  :)

---

### Post by Pumalite on 2008-09-05
XP or Vista?
If Vista; allocate space for Ubuntu with the Vista partitioner first.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by gr3y5t0ne on 2008-09-06
It's XP, unfortunately..

---

### Post by Pumalite on 2008-09-06
Fornumately. You can use the Live CD and it's partitioner. Burn a new CD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Do md5sum on the iso, burn at 4x or less, check CD integrity before install. Do not use CD-RW (I'd get rid of the RAID 0; minimal performance enhancement; lost of headaches)

---

### Post by gr3y5t0ne on 2008-09-08
thanks, i'll try that!

---

### Post by gr3y5t0ne on 2008-09-12
i tried that, but it still came up with the same thing. i have roughly  250GB used up on Windows XP, and i don't want to get rid of that. is the alternate install CD any use?

---

### Post by Pumalite on 2008-09-12
The Alternate CD is not going to resolve your space problem

---

### Post by mclarenracer on 2008-09-12
Hey im having the same problem, wont even let me do a manual install either. Im using a hp pavilion (desktop), and have used the same cd on my laptop, so its not a burn error. I was also unable to get past the partition editor on a 7.10 cd i have.

---

### Post by Pumalite on 2008-09-12
Post your specs. (memory, graphics, etc)

---

