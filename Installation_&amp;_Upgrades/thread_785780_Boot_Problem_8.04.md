---
title: "Boot Problem 8.04"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by ostrowlaw on 2008-05-07
Hi,

My brother in law came other with his Ubuntu 8.04 box last night.  I am NOT a real Linux person so please pretend you are posting for a blonde here (LOL).

The machine starts, but will not boot, no screen, no Linux.  I can boot from the CD, but not from the hard drive.  I need to reinstall the boot sector (or whatever Linux calls it).

I looked at the System on the Linux menu, but could not find anything for reinstalling boot sector, etc.

Is there something on the disk or, once started from the disk, in the menus, for doing this or do I need to totally reinstall Linux from scratch.

Thanks for your help.

Blonde Alan
:shock::shock:

---

### Post by Pumalite on 2008-05-07
This might help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ostrowlaw on 2008-05-07
Thanks, but this is a pure Ubuntue 7.04 installation, no Windows.  I went through the installer and I am quite "chicken" to write over anything as I'm not really sure what I'm doing.

Thanks
Alan

---

### Post by Pumalite on 2008-05-07
OK. Boot your Live CD and post from the Terminal:
sudo fdisk -l
(copy and paste the output here)

---

