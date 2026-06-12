---
title: "boot.img.gz on usb looks for an iso installer"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by nyinge on 2006-12-17
```
 zcat boot.img.gz > /dev/sda 
```

boot.img.gz file from [here]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/boot.img.gz").

Things seem like a normal install until it reaches the step, "Scan hard drives for an installer iso image."  It seems to actually scan for an iso on HDs and on the usb stick.  I've placed an iso file at their root directories, but it still failed with a not found error.  Any other work around this, or where am I supposed to place the installer iso file specifically?

---

### Post by tkjacobsen on 2006-12-18
If you use the boot.img.gz from netboot:
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/boot.img.gz)

Then you can install ubuntu entirely from the usb (if you have a working network connection)

---

### Post by mgchan on 2006-12-29
> **nyinge said:**
> ```
 zcat boot.img.gz > /dev/sda 
```

boot.img.gz file from [here]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/boot.img.gz").

Things seem like a normal install until it reaches the step, "Scan hard drives for an installer iso image."  It seems to actually scan for an iso on HDs and on the usb stick.  I've placed an iso file at their root directories, but it still failed with a not found error.  Any other work around this, or where am I supposed to place the installer iso file specifically?

Been having the same error.  I didn't follow the install from usb instructions exactly, since I already had a syslinux usb drive running DSL.  I had the iso in both my usb root drive and my windows C drive.  I don't think network install works for me, since I only have wireless access at the moment and I don't think my ipw2200 WiFi is supported without building additional modules.

Edit: just saw in another thread that apparently this only works with the alternative iso - I have the desktop.  Not sure why this is, but I'm grabbing it off the torrent right now.  Will let you know if it changes things.

Edit #2:
Posting this from Ubuntu...check out [HOWTO: Install Edgy 6.10 from an .iso file]("http://ubuntuforums.org/showthread.php?t=316093").  Apparently, when you get to the point that the installer cannot find the .iso file, you need to switch over to another terminal (CTRL+ALT+F2), press enter to start the shell, then enter the following:

```

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0
```
This got it to work for me!  Off to tweak...

---

### Post by perfectopresents on 2007-01-07
why on earth should 

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

be required to install form hard disk? It seems rather band-aid like to me, a work around to fix a situation overlooked in the development of the installer. Furthermore, although the Ubuntu installation pages seem to indicate that ubuntu may be installed from the hard disk, it doesn't go into a great deal of details, and the little detail above in particular seems conspicuously absent even though any attempt to install from from a linux partition inevitably fails without it. Just a little bit irritating, is all.

Aside from that, I have some issues with the lack of clear communication by the installer software to the user about how to go about installing to an existing partition that has already been formated and prepared by an earlier installation of another linux distribution, such as in the case of a multi-distribution installation that I am presently attempting. I have read that there is still a need to do the partition step in order to mount the root partition, but that isn't clear in the ubuntu installer which sounds like it might want to nuke the whole disk.

---

