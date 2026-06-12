---
title: "Installing Ubuntu on loopback filesystem: possible?"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by psyke83 on 2005-11-05
Hello,

I'm curious if it's possible to install Ubuntu Breezy on a loopback filesystem? Let me be more precise. I have a Dell Inspiron 8000 laptop running Windows XP. I have previously repartitioned the (small, 10gig) drive and installed Ubuntu 5.10, and it worked pretty well, but there were some issues with applications and the graphics card driver (the system would freeze badly when the X server quit). I'm willing to install Breezy again, but I have very little space on the hard drive, and unfortunately I can't just throw out XP because I depend on some applications (and games :)).

Before I say any more let me anticipate some "why bother" remarks. First of all, my laptop has very little drive space, and I install and uninstall applications in XP a lot, but sometimes for certain projects I need a lot of space, and in these instances Linux may need to be removed. Basically, it's a big hassle using ntfsresize/fdisk to repartition every time I have to do this, and managing a loopback file on the NTFS partition would be a lot simpler. Secondly, using the Live CD isn't an option for me. My CD-ROM drive is flakey and doesn't work well in continuous read mode, and because my system memory is low (196mb), opening large applications (eg. OpenOffice.org) slows the system to a crawl from paging/CD accessing.

Sorry for the rant, here's my needs: I want to install Ubuntu in a loopback filesystem on my NTFS partition. Has anyone done this, and can they confirm if it works/what I need to do? I understand that R/W support for NTFS is very buggy, but according to my understanding, there's two versions of the NTFS kernel module - the old version, which is unreliable/unusuable for R/W operations, and the new module, that pretty much only supports R/W in overwrite mode (modifying already existing files). Theoretically, the new driver should allow me to mount and access a loopback on a NTFS partition, right?

Check out this: [http://marc.theaimsgroup.com/?l=linux-kernel&m=103089008129720&q=raw](http://marc.theaimsgroup.com/?l=linux-kernel&m=103089008129720&q=raw)

That seems to describe precisely how to go about doing what I want, but I'm unsure how to proceed. Can anyone offer some assistance to install Ubuntu in this way? :)

Any help would be appreciated, and I think if this is done successfully it could be streamlined to introduce Windows users to Ubuntu with less hassle (well, eliminating the need to repartition :))

Regards
psyke83

PS. If there is a more suitable forum to post this message please let me know, it's my first post here! This is an excellent community and this forum has been an excellent resource since I started using Ubuntu a few weeks ago.

---

### Post by SickTwist on 2005-11-06
Unfortunately I don't have any insight to share regarding how to do what you propose. However, wouldn't a loopback filesystem take approximately as much space as it would just to give Breezy its own partition? I'm not sure I understand what the advantage would be in performing the installation as you suggest. Ubuntu only uses about 2 GB of space for the full install. Is a 3 GB partition more space than you can spare from your XP installation?

---

### Post by psyke83 on 2005-11-06
Hey SickTwist,

Yes, I'm aware that it would take the same amount of space, but there's a big difference between using ntfsresize and fdisk to delete and resize partitions versus deleting a file from within Windows. I had some issues with Breezy and my hardware and I want to have the option to wipe and start from scratch, and as I said, sometimes I need to free up space for Windows.

Having read the link in my previous post, one needs to use a floppy or usb device to boot a minimal kernel to mount the loopback. However, I would be happy to create a small-ish partition for "/boot" to keep permanently, that would reduce the hassle of booting into a loopback filesystem perhaps.

psyke83

---

