---
title: "Full system on USB stick with installer option"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by Thystra on 2010-07-20
I would like to make a bootable Ubuntu system on a USB stick from a full install, so I can update the packages/kernel etc, and I would also like to have the ability to Install ubuntu from the USB stick onto other computers.  

What package allows you to run the installer that is found on the LiveCD?

Also, is it possible to have a Ubuntu installer that uses updated packages rather than the LiveCD so they are current when installed rather than the release packages to save on the download/updating time?

Thanks.

---

### Post by ajgreeny on 2010-07-20
If you have the .iso of a ubuntu version on your hard disk simply run **System ->Administration ->Startup Disk Creator**, pick the iso and your usb drive and it will do it all for you.  You can choose whether to reserve some space on the usb drive to save documents and settings, or to discard them and use it just like a live CD.

I'm not sure about the updates that you ask about, as I have only ever used it simply instead of a live CD to install on a netbook without a CD drive.  If you reserve enough space on the usb, I suppose it may be possible, but I just don't really know.

The alternative is to use remastersys to produce your own live CD, but again I have never used it, only read about it, so can give you no more info than the name.

---

### Post by C.S.Cameron on 2010-07-20
It sounds like you want Remastersys:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by Thystra on 2010-07-21
Well, I don't think remastersys is quite what I want.  I looked at that.  What I think I want is Ubiquity - the actual installer package.  

If I set up a full install (not livecd/liveusb) on a USB Stick and install Ubiquity, will I be able to install Ubuntu on other computers from the USB system and it not being a live CD? or what would be needed to do that?

---

### Post by C.S.Cameron on 2010-07-21
You could do a Full install to one partition and put the live iso on another then get grub2 to boot either.

---

