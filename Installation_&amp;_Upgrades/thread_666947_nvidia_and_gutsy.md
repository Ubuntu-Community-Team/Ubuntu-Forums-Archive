---
title: "nvidia and gutsy"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by bkelly on 2008-01-13
I am having trouble with my nvidia card, discussed in the section on video.  I downloaded the Ubuntu 7.10 install and don't know how to burn it to disk.  I found another thread that said to use this command to burn the disk:
cdrecord dev=0,0,0 -data speed=48 ubuntu-7.10-desktop-i386.

The only thing I changed was the file name on the end.  The computer responded with:

The program 'cdrecord' is currently not installed.  To run 'cdrecord' please ask your administrator to install the package 'cdrecord'

I cannot burn a CD without installing software?  

I am new to Linux and have a DVD and CD device installed.  How do I determine the /dev/xxxx that picks each drive.  I looked in /dev and was not able to figure it out.

So how do I get the image burnt to a CD.

---

### Post by Sef on 2008-01-13
> So how do I get the image burnt to a CD.

I use GnomeBaker.  It works great when burning CDs.  Applications > Add/Remove > set top right box to all available applications (if it is not) > search > type in GnomeBaker > apply > apply > close

---

### Post by MCBTunes on 2008-01-13
Ok, I am going to make an assumption first. That you downloaded the 7.10 image with windows XP/Vista. You will need burning software, I used Nero but any program that will burn a .iso image is fine. You put the CD in, select burn as image, select the 7.10 .iso file and burn it to a CD.

You will then have an Ubuntu 7.10 bootable CD.

As far as the graphics card goes... I am struggling getting 7.10 to work with my 8800GT so I'm not much help there.

---

### Post by PmDematagoda on 2008-01-13
MCBTunes, what problems are you having with your Nvdia 8800GT card?

---

