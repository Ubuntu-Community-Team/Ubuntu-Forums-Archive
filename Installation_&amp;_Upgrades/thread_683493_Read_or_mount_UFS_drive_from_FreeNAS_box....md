---
title: "Read or mount UFS drive from FreeNAS box..."
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by s1mple_M4N on 2008-01-31
Hi all, I've looked around here and googled for information on this but I'm a bit stuck and hoping someone can help me out...

Until last week I had a FreeNAS server on my home network with a 160GB SATA drive holding mp3/photo/movie files formated to UFS.

Due to issues of economy, I have installed the SATA drive on my main PC and reinstalled Feisty. I was aware there were issues with UFS drives on Linux, but from what I have read they are readable with the correct kernel setup.

My problem is I'm not 100% sure how to go about making the drive readable so I can gather the data and format the drive to a useable filesystem for Ubuntu.

If anyone can point me in the right direction, and suggest the ideal file system (ext3?), I would be very grateful.

Also, is there a way to mount the disks so they appear in nautilus at boot??

Thanks in advance,

RoyJ

---

### Post by Craigus on 2008-01-31
> I had a similar problem trying to mount by OpenBSD partition from Ubuntu 6.10.

The solution turned-out to be to specify the read-only option in the mount command-line, as follows.

mount -r -t ufs -o ufstype=44bsd /dev/sda4 ./tempo


thanks jcookeman
louisgag is offline   	  	Reply With Quote

from this thread:

[http://www.linuxquestions.org/questions/bsd-17/cannot-mount-freebsd-ufs-from-linux-191184/]("http://www.linuxquestions.org/questions/bsd-17/cannot-mount-freebsd-ufs-from-linux-191184/")

---

### Post by s1mple_M4N on 2008-01-31
Thanks Craigus

I eventually got it done with that command. I had to type /dev/sda1 instead of /dev/sda as I had been.

Once I get all the data off the drive, I want to format it ext3 or whatever, but is there something I have to add to /etc/fstab to automount it at boot??

---

