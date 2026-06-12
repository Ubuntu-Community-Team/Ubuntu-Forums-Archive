---
title: "Installation from flash drive"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by Marcel_Garland on 2014-06-24
I am using my laptop which has the "no bootable device error. So i tried to use a bootable flash drive with Ubuntu on it. I tried to boot my laptop with the usb drive but it says "syslinux 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et al" How do i fix this please help me

---

### Post by yancek on 2014-06-24
> I tried to boot my laptop with the usb drive but it says "syslinux 4.07  EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et al" 

That will show on any Linux CD/DVD/flash drive booting with isolinux/syslinux.  It's just an informational message, not a problem.  The problem is what comes after, in your case is it nothing?  or something you did not mention, a black screen with no progress?

Have you tried your "bootable flash drive" on another computer successfully?

---

### Post by Marcel_Garland on 2014-06-25
thats all it says nothing comes afterwards and no i didnt try the installation on different laptops, but that sounds like a great idea and im gonna try that

---

### Post by Bucky Ball on 2014-06-25
Welcome. When it stops at the message, is there a flashing cursor? I suspect not, but best to ask. ;)

How did you burn the USB, did you burn using Win or Ubuntu install, and which flavour/release of Ubuntu are you attempting to install?

Be nice to know if it boots on another machine, certainly. Big question is why it's not booting on this one. Did you check the downloaded ISOs M5Sum? Safest way to get the ISO is via a torrent.

PS: Sorry about accidentally flooding the thread. Server issues my end. Rectified now. ;)

---

### Post by Marcel_Garland on 2014-06-26
hmm the flavour i used was 12.04 LTS 32 bit. next im gonna try 64 bit. i will also check the m5Sum

---

### Post by yancek on 2014-06-26
It would be helpful if you still need assistance to indicate what software you used to create the bootable flash drive.

---

### Post by Marcel_Garland on 2014-07-01
i used pendrive linux. I tried again today and i used the 32 bit version which did the same exact thing. Any recommended software i can use?

---

### Post by sudodus on 2014-07-01
Remember to check the md5sum versus the listed value at

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You can try Unetbootin. See these links, one general and one specific

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[URL="http://zleap.net/unetbootln-usb-how_to/"]Paul Sutton's Unetbootin how to
[/URL]

---

