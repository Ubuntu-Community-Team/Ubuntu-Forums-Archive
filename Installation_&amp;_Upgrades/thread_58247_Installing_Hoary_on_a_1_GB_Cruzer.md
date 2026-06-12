---
title: "Installing Hoary on a 1 GB Cruzer?"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by baslow on 2005-08-19
[This squib in Engadget](http://www.perl.com/pub/a/2000/10/gnome.html) says that it should be possible to install Knoppix "or whatever" on your own USB 2.0 flash drive, creating a homegrown "computer-on-a-stick".  I have a 1 GB SanDisk Cruzer Mini.  Would installing Hoary be as simple as attaching the Cruzer to my PC, inserting the install disk, rebooting my PC and, assuming it detects the Cruzer, directing the installation there?

Has anybody done this?  Any tips or warnings?

Thanks.

---

### Post by macgyver2 on 2005-08-19
[QUOTE=baslow][This squib in Engadget]("http://www.perl.com/pub/a/2000/10/gnome.html") says that it should be possible to install Knoppix "or whatever" on your own USB 2.0 flash drive, creating a homegrown "computer-on-a-stick". I have a 1 GB SanDisk Cruzer Mini. Would installing Hoary be as simple as attaching the Cruzer to my PC, inserting the install disk, rebooting my PC and, assuming it detects the Cruzer, directing the installation there?

Has anybody done this?  Any tips or warnings?

Thanks.[/QUOTE]
I've been looking in to doing this for some time and right now I'm actually in the middle of a Linux From Scratch install on a 1 GB flash drive.

One warning I've come across a few times...flash memory can only handle a limited number of writes. The number I see quoted all the time is one million. That means heavy logging, or if you use part of the drive for swap, or if the filesystems on the drive are mounted with the atime option, or probably other things I'm missing/don't know about...any of that could mean that you might destroy your flash drive rather quickly. That doesn't mean you can't do it, it just means you probably should take precautions. Use the noatime mount option and don't put a swap partition on the drive (not sure why you'd do that anyway...it would eat into the 1 GB...not really worth it). Also, on another board someone suggested making /var/log a ramdisk. I had been thinking of something more along the lines of linking to /dev/null. I just want to do this project to see if I can do it...after that I'll probably just use it for rescue purposes if I ever need to, so I don't really care about logging. I'm still researching that part of it.

Anyway, good luck if you decide to go forward with it.

---

### Post by baslow on 2005-08-19
I've thought about it a little more and I realize that what I really want to do is install the Live CD version of Hoary to my flash drive, for two reasons:

1) since the point of a computer-on-a-stick is to be able to use it with different computers I'll want the Live CD's ability to configure itself to whatever PC it is booted on; and

2) I'm guaranteed that the installation is no more than 650 MB.

The only way I know to create a live CD version of Hoary is to burn an ISO file to a blank CD. How does one install it to a USB flash drive?

---

### Post by baslow on 2005-08-19
[This page in the Ubuntu Wiki](https://wiki.ubuntu.com/OEMRescue) , about creating a special Rescue edition of Ubuntu, seems to suggest that nobody has gotten Ubuntu booting from a USB stick yet...

Oh, well...

---

### Post by macgyver2 on 2005-08-19
[QUOTE=baslow][This page in the Ubuntu Wiki]("https://wiki.ubuntu.com/OEMRescue") , about creating a special Rescue edition of Ubuntu, seems to suggest that nobody has gotten Ubuntu booting from a USB stick yet...

Oh, well...[/QUOTE]
Keyword there is "yet"...your "oh, well" sounds a little like defeat...but maybe you can be the first to do it! :)

Google around for anything about people who might have succeeded with Knoppix.  Also, look around on the Gentoo forums or wiki.  Back when I used Gentoo more, I think I came across a few threads where people had posted about being succesful making a Gentoo LiveUSB.  You might be able to use their successes (if they describe how they did it) to fill in the gaps you need to for a Ubuntu LiveUSB.

---

