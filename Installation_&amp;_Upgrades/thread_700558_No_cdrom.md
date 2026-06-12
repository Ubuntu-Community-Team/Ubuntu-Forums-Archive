---
title: "No /cdrom?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by AdHavoc on 2008-02-18
So I just installed Ubuntu 7.10 on an old Dell Precision 410 to mess around with, and now I'm trying to get it to connect to my wireless network via a Linksys WUSB11 2.6.  In order for it to recognize it, I need the windows drivers and also ndiswrapper.  ndiswrapper is on the Live CD that I put in the CD drive (I have two drives), and the Live CD Repository is checked in Synaptic.  However, when I try to install ndiswrapper from the cdrom, it says I need to insert to Live CD into /cdrom and try again.  I have tried putting the CD into both drives, to no avail.  I do, however, know that the drives work as I installed ubuntu from one of them.  Any suggestions?

Thanks!

---

### Post by Pumalite on 2008-02-18
Check in /dev and see if you have a cdrom device loaded. Check also your BIOS for CD-Drive settings.

---

### Post by frogbots on 2008-02-18
I have had a similar problem after upgrading to 7.10.  My post did not gather any insight as to what was causing the problem, but further searching into other questions presented me with the following information.  Not my information, I have copied it for you and others.  This solution worked for my cdrom -- I hope it helps

Duane

Here:

************
edit /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

**************

Credit for this 7.40 slow boot fix goes to "Fabio Povoledo". He had it posted in a forum somewhere and I was days finding the solution. I saw a lot of people trying to fix the slow boot issue. I assume none of these people could do a fresh 7.10 install.

---

