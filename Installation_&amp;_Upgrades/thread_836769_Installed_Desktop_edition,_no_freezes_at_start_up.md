---
title: "Installed Desktop edition, no freezes at start up"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by peroija on 2008-06-21
I had trouble installing the latest desktop v8.*, it would freeze before installing so I switched to the alt. version (textbased) and it installed everything.  It then spit out the CD as should be expected to do a reboot.  The computer rebooted and then the Ubuntu loading bar came up and it froze at roughly 95%.  I let it sit there for 1hr and nothing happened, totally frozen.  I restarted my computer, this time it froze at 45%.  It keeps freezing at the load screen.  What do I do?  I am the greenest of green newbies for Ubuntu so I need some help.  THANKS!

---

### Post by Pumalite on 2008-06-21
Post your specs.

---

### Post by peroija on 2008-06-21
Intel Pentium 4 2.4ghz
1024mb ram
40gig hard drive
NVIDIA GeForce FX 5500
Dell Dimension 2350

---

### Post by damphoud on 2008-06-22
Reboot into Ubuntu, and when you start to load, switch into tty1 and see if you run into an error. If so, post/research the error.

---

### Post by peroija on 2008-06-22
tty1? I don't understand.  Please remember that I am very very very new to ubuntu linux. Thanks

---

### Post by real_ate on 2008-06-22
he just means push CTRL-ALT-F1 to get to tty1

---

### Post by Pumalite on 2008-06-22
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by peroija on 2008-06-22
below is the ctrl-alt-f1 (sorry for the large size):

[IMG]http://www.pitt.edu/~kmh88/S3700078.jpg[/IMG]

as for the other message, is the live cd the one that allows you to try out Ubuntu without installing?  If so that does not load for me, it just freezes so I am not sure how where to type the sudo message

---

### Post by Pumalite on 2008-06-22
Try a Knoppix Live CD:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by peroija on 2008-06-22
Okay, I am downloading it right now.  What will this disc accomplish?

---

### Post by Pumalite on 2008-06-22
It's supposed to recognize all hardware easier and mounts all your drives/partitions automatically at boot
From the corresponding partition, post:
cat /boot/grub/menu.lst
sudo fdisk -lu

---

