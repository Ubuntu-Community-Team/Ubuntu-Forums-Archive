---
title: "2 identical PC's - need to copy xorg file on usb - how?"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Ozdemon on 2007-11-20
I have 2 identical computers that have identical software, including Ubuntu version (7.04).  Somehow, the xorg file on one is screwed and the backup is not right.  So, I need to make a backup on the good PC and copy the file to a usb stick and then put it on the sick PC.

Can anyone help with the commands to do this?

Thanks in advance.

---

### Post by Craigus on 2007-11-20
On the working machine:

> sudo cp /etc/X11/xorg.conf /media/whatever-your-usb-stick-mounts-as/xorg.conf

On the broken machine:

Log in to a terminal (you can do the recovery mode option in grub). Then:

> sudo cp /media/whatever-your-usb-stick-mounts-as/xorg.conf /etc/X11/xorg.conf 

if the stick doesn't automount in recovery mode, mount it first:

> sudo mount /dev/sdb1 /media/whatever-your-usb-stick-mounts-as

---

### Post by Ozdemon on 2007-11-20
Worked like a charm.  :grin:

Many thanks for your accurate and prompt reply.  =D>

---

