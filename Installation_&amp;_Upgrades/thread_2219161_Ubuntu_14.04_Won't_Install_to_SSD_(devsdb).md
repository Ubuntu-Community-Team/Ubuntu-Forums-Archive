---
title: "Ubuntu 14.04 Won't Install to SSD (/dev/sdb)"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Mitchell_Green on 2014-04-23
Hi,

I have a laptop with a 1TB HDD and a built in 16GB SSD which was originally used by windows as express cache.

Some time ago I decided to disable this and install Ubuntu 13.04 to the 16GB SSD. Since then I have upgraded to Ubuntu 13.10 and this setup has never given me any issues. 

However, when I tried to do a fresh install of Ubuntu 14.04 from an installation DVD the installer would not allow me to install to the built in SSD and threw an error that said something to the effect of "cannot install to a drive outside the disk". The error message, by the way, also would not close. 

Obviously the installer has some issue with me trying to install to /dev/sdb because it seems to think it is an external drive (which technically it isn't).  Before anybody asks, I tried to install the bootloader to both /dev/sda and /dev/sdb. It didn't make a difference.

If anybody could offer some assistance it would be hugely appreciated as I would like to use my SSD again. Thanks very much.

---

### Post by Double.J on 2014-04-23
Hi there!

This is a strange situation as ubuntu is actually fine installing to an external usb stick as well as an internal device.

I would say that first port of call would be to re-download and recreate the installation disk; sometimes these errors are cause by a fault in copying the ISO.

I usually also disconnect all drive apart from the one I'm trying to install to - you can always update grub later. 

Finally I would  suggest  copying any data left on the ssd and reformatting it including the partition table?

Jj

---

### Post by Mitchell_Green on 2014-04-23
Okay, so I created a live USB disk to use as a new, uncorrupted installation medium and tried to install to the SSD again and I got the same error message as last time, which was about the 3rd/4th time in a row.

Then I decided to try one last time for the hell of it before resigning and installing an older version to the SSD and using that as a platform from which to upgrade and, believe it or not, it magically decided to work. I must have been experiencing some weird bug triggered by a particular sequence of events. 

Anyway, the installation was successful and I am now running 14.04 off the SSD. 

Thank you very much for your assistance earlier, it was much appreciated! In the end it seems I was the victim of some anomaly or other. Thanks again.

---

### Post by Double.J on 2014-04-23
Hey there,

really glad to hear it's working.

I was thinking on u way home that I did have one machine around about 12.10/13.04 that would not install at all on any drives on my expansion card. The release before and after had no problems, but I had to plug the drive into the main board directly and then it installed and then ran off of the expansion cad with no errors!

all the best,

Jj

---

