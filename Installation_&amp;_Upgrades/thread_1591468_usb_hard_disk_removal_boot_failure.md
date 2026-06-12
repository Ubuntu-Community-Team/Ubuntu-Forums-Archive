---
title: "usb hard disk removal boot failure"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by chrisclay on 2010-10-09
Hi i have remove an external hard disk from my Ubuntu server and it will not boot unless i connnect a keyboard and moniter to it and press skip as it still trying to load the usb hard disk
 
please an someone tell me how can i prevent  this occuring
 
thanks chris

---

### Post by efflandt on 2010-10-09
Did you boot from the USB drive, or was it just mounted for data?

Check /etc/fstab and see it that was trying to mount it.  Comment out that line by putting # at the beginning of that line (with **gksu gedit** or **sudo nano**).

If the USB drive has bootable regular system, is grub on your main drive (or BIOS) still trying to boot the USB?

---

### Post by chrisclay on 2010-10-10
Hi thanks for your help it is all working fine now thanyou

---

