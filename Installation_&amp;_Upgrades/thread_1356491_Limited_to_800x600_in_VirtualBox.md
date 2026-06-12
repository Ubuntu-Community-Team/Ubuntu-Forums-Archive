---
title: "Limited to 800x600 in VirtualBox"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by JimStewartBrown on 2009-12-16
Can anyone help me understand why virtualbox limits Ubuntu to 800x600?  

I am running virtualbox on a Core2duo with 6Gb RAM and 64bit Windows Vista SP2, and an nvidia geforce 9600M with 512Mb.

The annoying thing is, out of the box, Mandriva 2010.0 and OpenSuSE 11.2 will run full screen (actually corner to corner of laptop monitor) and ubuntu 9.10 x64, my preferred distro, is stuck at 800x600.

When I tell VB to use fullscreen, it just blacks out everything around the 800x600 square.  In Ubuntu, under prefernces, the resolution choices are limited to 800x600 and 640x480.  The other distro's had other (higher res) options available in the appropriate settings location.  My VB is set up with 3Gb RAM, and 128Mb video memory.

Any thoughts?

---

### Post by llawwehttam on 2009-12-16
In the virtualbox setting enable 3d acceleration.

then erm ... try installing the drivers for your card.

---

### Post by mikewhatever on 2009-12-16
As far as I know, you have to install guest additions in your Ubuntu guest.

---

### Post by JimStewartBrown on 2009-12-16
I have already enabled 3d acceleration in the virtualbox settings.  I am unsure how to upgrade drivers for my card in Ubuntu in virtualbox.  I went to System>Admin>Hardware drivers (where I find it on any physical computer, and it tells me I need "x" driver i.e. nvidia 190 . . .), but it tells me it finds none.

Is there a "special" virtualbox video driver I'm missing?

Thanks in advance!

---

### Post by mikewhatever on 2009-12-16
> ................

Is there a "special" virtualbox video driver I'm missing?

Thanks in advance!

Yes, it's called guest additions.
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

