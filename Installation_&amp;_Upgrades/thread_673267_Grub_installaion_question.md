---
title: "Grub installaion question"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by migrax on 2008-01-20
I want to install Ubuntu on a pc for testing purposes, and I need to install it on a separate hard drive from my windows install, and not overwrite my mbr. Is there a way to do this at installation time, I tried it earlier this week and saw an advance options button. I merely stated that I could opt to install to (hd0). What would I change this to if I wanted to boot from the third partition (slave) of my second IDE drive? This will be a primary partition.

Thanks in advance


migrax

---

### Post by logos34 on 2008-01-20
**(hd1,2)** should work, but it's safer to use the /dev/<drive> form:

When you come to the partitioning stage, note how the slave drive is designated. (it may be sdb or hdb).  Then on the 'Ready to install' screen click 'Advanced' button and replace (hd0) with **/dev/hdb**, or whatever the drive is seen as.  This will assure it goes on the mbr of the primary slave drive. 

Choose to continue using the live cd after installation completes.  Mount root partition in Places>computer (should do so at /media/disk), then open menu,lst up to edit:

gksudo gedit /media/disk/boot/grub/menu.lst

Change the 'groot' and 'root' lines to (hd**0**,2).  (assuming root is on the third partition).  You need to do this because as soon as you switch the Bios to boot the slave drive first, it becomes 'hd0'.

If you want to boot windows on the other disk from grub, see [this.]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

You could also send grub to a floppy by replacing the '(hd0)' with **(fd0)**.

---

### Post by eggdeng on 2008-01-20
hd1,2

---

