---
title: "adding Jaunty to grub menu"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nzkronic on 2009-04-09
Hi, I have just made a new parition (sda2) which has a install of the 9.04 beta, however I start up my grub menu and only have my 8.10 (sda1) showing on the grub boot list. 

What entry do I need to put in my menu.lst file to allow me to choose this OS when entering the grub boot menu.

I can view files on my new partition through my old install of 8.10, if I need to track some files down I can.

This is what shows in the Jaunty boot folder if this helps
/media/disk/boot$ ls

abi-2.6.28-11-generic     System.map-2.6.28-11-generic
config-2.6.28-11-generic  vmcoreinfo-2.6.28-11-generic
memtest86+.bin            vmlinuz-2.6.28-11-generic

title		Ubuntu 9.04 Beta
root		(hd0,1)?
kernel		?
initrd		?

---

### Post by inobe on 2009-04-09
you could have used gparted to shrink and run the dual boot setup.

---

### Post by nzkronic on 2009-04-09
ok, I did pick the dual boot option to begin with but it had an error, so I just wiped my XP Partition,  will try remove the partition so i have free space and start again.

---

### Post by inobe on 2009-04-10
[http://www.youtube.com/watch?v=JBfl3oViny8&feature=related](http://www.youtube.com/watch?v=JBfl3oViny8&feature=related) :lol:

good luck

---

