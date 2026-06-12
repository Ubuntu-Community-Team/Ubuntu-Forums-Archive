---
title: "Choice of external drives"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by webdfeet on 2012-02-07
I'm looking at getting an external hard drive for my computer, to put the Ubuntu OS on it. I understand these will handle the operating system perfectly well. However, I'm wondering whether some makes of external drive might be better than others...reason being, I noted the long lists of incompatible hardware and became concerned.
I run a Dell Vostro pc, currently with WindowsXP on the main internal hard drive which I need to retain at this time. I've been looking at Seagate and also Western Digital external drives, 500GB (maybe higher).
Can I assume that these drives would be fine for installing a Ubuntu os on? My pc has USB2.0 slots. I've already tried out Ubuntu to some extent by booting from the CD and using the BIOS to do so, everything worked fine so I feel happy with how to proceed with installing.

---

### Post by plucky on 2012-02-07
> Can I assume that these drives would be fine for installing a Ubuntu os on? My pc has USB2.0 slots. I've already tried out Ubuntu to some extent by booting from the CD and using the BIOS to do so, everything worked fine so I feel happy with how to proceed with installing.


You can install on an external HDD,but the big question is Can you boot from an external USB drive?

If you can boot from a USB drive,you can then install GRUB to the MBR of the external and just change the BIOS to boot the external drive and leave your internal drive untouched.

Good Luck

---

### Post by webdfeet on 2012-02-07
> Can you boot from an external USB drive?

Good point; how would I be able to find out before committing cash to a piece of kit?

---

### Post by mastablasta on 2012-02-07
you burn ubuntu image on USB key (1GB size stick is enough) and then try to boot from it.
 
to put Ubuntu on the key use 
 
LinuxliveUSB 
or 
Unetbootin
 
also if you plant ot use Ubutnu sort of occasionally it's cheaper to install it (complete install) to 8 or 16 GB USB key.

---

### Post by efflandt on 2012-02-09
A couple of things to note.

During the partitioning part of install, select "Other" which lets you set up whatever partition(s) you want on the external drive.  **But more important** is that you look lower down on the partitioning screen and select to install grub on the mbr of external drive (instead of default to mbr of your internal drive).

Even though you can change boot order in BIOS to USB before internal, you may still have to press F12 during BIOS splash screen to select the external drive.  That may be a safety feature to not accidentally boot something you do not intend to, like possibly a malicious bootable CD, etc.  The only virus I ever caught was a boot sector virus spread by infected floppies when I accidentally booted one that I had left in the PC while transferring files.

---

