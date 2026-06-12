---
title: "Partition Question"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by OmegaMB on 2008-08-11
My computer has one hard drive that has two partitions on it. The C: drive contains my Windows installation, while the D: is a Windows XP restore drive. If I were to install Ubuntu, would I be able to install Ubuntu to the C: partition and keep the D; partition untouched, so that if I ever had to reinstall Windows, I would be able to?

---

### Post by sandysandy on 2008-08-11
broadly u may consider this

de-fragment ur windows drive.

backup important data.

with gparted live CD <[COLOR="Red"]http://gparted.sourceforge.net/[/COLOR]> compress ur c:/ drive and in the free space make one partition (ext3) for Ubuntu and one more for SWAP.

here is gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

here is link for dual booting windows & ubuntu

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

regards

---

### Post by castor_troy on 2008-08-11
Free up space on your C: drive. Atleast 10gb for a Ubuntu. Boot with the Ubuntu live CD. Choose install option. You can resize your C: drive easily in a graphical and allocate as much space as you want to Ubuntu. Your D: drive will be untouched.

Cheers !

---

### Post by SkonesMickLoud on 2008-08-11
There's also [Wubi]("http://wubi-installer.org/").

---

### Post by tarps87 on 2008-08-11
You would be able to install to just the c: partition, but having never tried I don't know if the backup util would work as the C: part of the hard drive would be a different format after installing ubuntu.  It may be possible to create a set of backup cds.

Edit: I forgot about the Wubi, this would probalbly be a good place to start as you can still use you windows os

---

### Post by sandysandy on 2008-08-11
tarps87 has a good point. with ubuntu 8.04 onwards the cd has everything on it to install within windows.

no hassles of partitioning etc. 

regards

---

### Post by tarps87 on 2008-08-11
Lucky SkonesMickLoud remembered.  Its how I introduced my brother to ubuntu

---

