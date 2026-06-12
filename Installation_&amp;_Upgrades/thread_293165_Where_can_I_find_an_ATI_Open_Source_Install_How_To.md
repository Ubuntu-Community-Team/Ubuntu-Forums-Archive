---
title: "Where can I find an ATI Open Source Install How To?"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by moeFinley on 2006-11-04
Can someone point me in the direction of a 'how to' for installing the open source ATI driver, preferable in Edgy.  I've tried searching but 'open source ATI driver' just seems to bring up results for the official ATI driver.

Thanks  :-D

---

### Post by pay on 2006-11-04
The driver is built into the kernel so if you compiled your kernel with support for it (I think that Ubuntu does) then just go to your /etc/X11/xorg file and change video the driver to radeon.

---

### Post by babooka on 2006-11-04
$sudo dpkg-reconfigure xserver-xorg

choose either "ati" (open source) or fglrx (close source).

It also depends on what car you've got.

---

### Post by moeFinley on 2006-11-05
It's that simple ](*,) 

So if I have the following in my xorg.conf i'm using the open source driver?  I don't know why it has the first bit with Driver "ATI"?  It doesn't work if I take it out though.

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver "radeon"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
	Option "AGPFastWrite" "on"
EndSection
```

---

### Post by acerlinux on 2006-11-05
I just install it again:

> 
sudo aptitude install xserver-xorg-driver-radeon


then I got it work very well.

If you wish to try Beryl and make the direct rendering work. I think you need to complete remove the fglrx driver, and reinstall the libGL package. that is what I did. and my old ATI 7500 works very well with only a trivial problem.

---

### Post by tagginannie on 2006-11-05
> **moeFinley said:**
> Can someone point me in the direction of a 'how to' for installing the open source ATI driver, preferable in Edgy.  I've tried searching but 'open source ATI driver' just seems to bring up results for the official ATI driver.

Thanks  :-D

check out the unoffical Ubuntu guide for [installing ATI drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Suzy

PS: I'm glad Suzy posted that link to Super Grub Disk, thanks Suzy!
wr0x2,

Your welcome ;)

---

### Post by Circus-Killer on 2006-11-16
> **tagginannie said:**
> check out the unoffical Ubuntu guide for [installing ATI drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Suzy


congratulations suzy, you successfully pasted a link to a howto explaining the official ati driver installation, as apposed to a guide for the open source drivers.

unfortunetly, i also cant find instructions on installing the open source drivers. however, if im not mistaken, when you install edgy, edgy automatically installs the open source ati drivers.

if i manage to find the howto i found a couple of weeks ago, ill post back here.

---

