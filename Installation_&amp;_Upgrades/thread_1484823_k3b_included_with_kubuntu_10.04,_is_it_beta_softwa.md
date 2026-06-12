---
title: "k3b included with kubuntu 10.04, is it beta software?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by wandalalakers on 2010-05-16
I noticed that when I click on help about in k3b is says 1.91.0.
Why is release candidate version included with a LTS version of Kubuntu?
On K3b's website, it points to this:
[https://sourceforge.net/projects/k3b/files/k3b/1.90.0rc1/k3b-1.90.0rc1.tar.bz2/download](https://sourceforge.net/projects/k3b/files/k3b/1.90.0rc1/k3b-1.90.0rc1.tar.bz2/download)
I've reported this and another problem to kde.org and launchpad.
This is kinda sad that I can't even continue multisession DVD-Rs that were created with a previous version of k3b.

I'm trying to continue burning a multession DVD-R that was created with a previous version of k3b.
I'm using kubuntu 10.04.
K3b prompts me to insert a suitable medium into the drive but it says it has found medium appendable dvd-r medium.



Debugging output:

Devices
-----------------------
ATAPI DVD A DH20A4P 9P57 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
ATAPI DVD D DH16D2P HP56 (/dev/sr0, CD-ROM, DVD-ROM) [DVD-ROM, CD-ROM] [None] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 376093 (770238464 bytes)

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.3 (KDE 4.4.3)
QT Version: 4.6.2
Kernel: 2.6.32-22-generic

Used versions
-----------------------
mkisofs: 1.1.10

mkisofs
-----------------------
Rock Ridge signatures found
376093

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 977424,1099216 -prev-session /dev/sr1 -gui -graft-points -print-size -quiet -volid linux backup -volset -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-david/k3bni3516.tmp -rational-rock -hide-list /tmp/kde-david/k3bzN3516.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-david/k3bPH3516.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-david/k3blE3516.tmp

---

### Post by wandalalakers on 2010-05-16
I booted a kubuntu 8.04 dvd and used k3b 1.04.  I was able to continue the
multisession DVD-R.  What I noticed is that when using k3b 1.04 it says it's
using growisofs when getting ready to continue the multisession dvd-r.
Kubuntu 10.04 says it's says it's using wodim.

A few days ago I download and compiled it but I still wasn't able to continue the multisession.
[http://cdrecord.berlios.de/private/cdrecord.html](http://cdrecord.berlios.de/private/cdrecord.html)

---

