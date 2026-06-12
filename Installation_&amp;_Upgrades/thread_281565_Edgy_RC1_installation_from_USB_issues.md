---
title: "Edgy RC1 installation from USB issues"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by uMax on 2006-10-21
Hi,

I am experiencing some issues installing Edgy RC1 from a USB stick (CDROM install is not possible as the PATA CDROM drive is not detected). I am using a Core2Duo with the ICH8 controller, two SATA disks and one PATA CDROM.

After getting the installer to run from the USB drive, I first ran into the issue that it could not find the file:

/pool/restricted/l/linux-restricted-modules-2.6.17nic-restricted-firmware-2.6.17-10-generic-di_2.6.17.5-10_amd64.udeb

I found out that the file was called:

nic-restricted-firmware-2.6.17-10-generic-di_2.6.17.5-10_amd64.u

on the USB drive (and also on the CD). Another one in the same directory is:

nic-restricted-modules-2.6.17-10-generic-di_2.6.17.5-10_amd64.ud

It seems that some filename limitation is hit there. I was at least able to rename them on the USB drive an continue.
Later I ran into the problem:

"Debootstrap Error" and "Failed to determine the codename for the release".

I could not really find a proper solution so far that worked (I searched the forum and the net).
Any help for finally getting ubuntu installed on my computer would be highly appreciated.

Thanks!

---

### Post by uMax on 2006-10-22
Hi,

I am posting this from my Edgy RC1 install...I managed to hardcode the distribution name into the script. Maybe not pretty, but it worked and helped me finish my installation. :mrgreen:

---

### Post by plut0nium on 2006-10-27
how did you manage to solve the distribution name problem, 'cause I have exactly the same :s

---

### Post by plut0nium on 2006-10-28
Ok, i found it in /var/lib/dpkg/info/base-install.postinst
(from what i remember)

---

