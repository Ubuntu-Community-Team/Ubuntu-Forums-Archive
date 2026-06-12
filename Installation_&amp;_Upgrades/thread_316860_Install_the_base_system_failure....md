---
title: "Install the base system failure..."
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by jexxie on 2006-12-11
Hi all, I've tried searching the forums / wiki for a relevant answer -- I haven't, thus the reason for the post.

I'm currently having problems installing either Edgy or Fiesty (both using the alternate cd), I get a error message when it's copying the first set of system files to the target install:
[http://dufault.info/Fail2.jpg](http://dufault.info/Fail2.jpg)

The error message on tty4 is this (sorry for the quality):
[http://dufault.info/Fail1.jpg](http://dufault.info/Fail1.jpg)

My relevant hardware is a P5B-VM motherboard, and I'm booting off a USB cdrom.  I have tried installing Dapper, it works fine oddly; I don't really want to dist-upgrade to Edgy, and then maybe to Fiesty again.

Can anyone shed some insight on this issue?

---

### Post by taurus on 2006-12-11
Did you check the integrity of the CD and how fast did you burn it?  Try burning it at a slower speed like 4x...

---

### Post by jexxie on 2006-12-11
I haven't checked the integrity of the CD, technically -- I have burned this cd-image three times, once on a CDRW (4X is the max), twice on a CDR, and I have checked the md5sum of disk image and burnt disk with the published MD5SUM, so I really have checked the data integrity.

Any more ideas?

---

### Post by K.Mandla on 2006-12-11
It looks like it's crashing out on pcmciautils. Is this a desktop machine?

---

### Post by jexxie on 2006-12-11
Yes, this is a desktop machine, it's a little mATX box. (with no cardbus whatsoever)

From the information on tty4, it looks like udev is having a problem with something, of what I have no idea.

---

### Post by jexxie on 2006-12-11
Also -- yes, I just ran the Feisty and Edgy disk checksum, it passes with flying colours.

---

### Post by jexxie on 2006-12-12
Well, through a long amount of hackery, I've installed Fiesty through VMware workstation (using the physical hd as the virtual disk,) Edgy still failed using the emulated devices (odd.)  One thing that I tries on the Fiesty install was that I ran /etc/init.d/pcmcia* stop, and the install went smoothly.  Since I haven't configured this install as anything important, I'll go try installing Edgy.

---

### Post by jexxie on 2006-12-12
Back again, no success.  I'm only able to install Feisty, be that good or bad...

I'd like to run Edgy preferably.

Anyone have any other ideas?

---

### Post by sebi k on 2006-12-14
As you might now, Edgy's kernel doesn't support the JMicron PATA controller and has also some problems with the Ethernet devices. I got the P5D-dlx and i could only install Small-Gentoo or Feisty.
Where did the installation of Edgy failed?

---

### Post by jexxie on 2006-12-14
Yes, I'm aware of the Edgy issues at hand -- I'm avoiding using the IDE controller by using a usb-cdrom.  Beyond that, I'm using a rt2500-based wireless card, so I don't mind about the onboard lan not working.

---

### Post by jexxie on 2006-12-18
*bump*

Anymore ideas anyone?

---

