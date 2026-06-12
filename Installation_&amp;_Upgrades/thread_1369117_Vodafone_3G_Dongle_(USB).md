---
title: "Vodafone 3G Dongle (USB)"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by rodst on 2009-12-31
I have installed Ubuntu and now need to connect to the Internet. I use a Vodafone 3G dongle (as I don't have a fixed telephone line) that works fine under Windows. However, when I try to install it under Ubuntu I get the following error message.
 
> 
[FONT=Comic Sans MS]Archive: /media/20071017_131019/setup.exe[/FONT]
[FONT=Comic Sans MS][/media/20071017_131019/setup.exe][/FONT]
[FONT=Comic Sans MS]End-of-central-directory signature not found. Either this file is not[/FONT]
[FONT=Comic Sans MS]a zipfile, or it constitutes one disk of a multi-part archive. In the[/FONT]
[FONT=Comic Sans MS]latter case the central directory and zipfile comment will be found on[/FONT]
[FONT=Comic Sans MS]the last disk(s) of this archive.[/FONT]
[FONT=Comic Sans MS]zipinfo: cannot find zipfile directory in one of /media/20071017_131019/setup.exe or[/FONT]
[FONT=Comic Sans MS]/media/20071017_131019/setup.exe.zip, and cannot find /media/20071017_131019/setup.exe.ZIP, period.[/FONT]

 
Does anyone have any experience of these Dongles and how to connect to the Internet please.

---

### Post by kevinatkins on 2009-12-31
Could you post back exactly what brand the dongle is?

Most of these USB modems actually also contain a small amount of flash storage on which windows setup files are located, so that under windows, when you plug the thing in for the first time, the relevant driver software is automatically installed for you. That's what you're seeing when you see the error message.

The trick is, the device needs to be 'switched' out of software install mode and into modem mode, and depending on the brand of device, there are linux utilities to accomplish this..

---

### Post by gneissprof on 2009-12-31
I am a Linux 'learner' and I have a similar problem.  I use a ZTE USB Modem on a Windows system.  I would like to use the (prepaid) USB modem on my Ubuntu 9.10 system.  Accordingly I shall follow this thread with interest.  In appreciation of any help.  Thank you.

---

### Post by phillw on 2009-12-31
Hi,

I have a 3G usb modem, which plugged in and was seen by my Ubutnu 9.04 and 9.10 systems. (It's also seen by 10.04, but that's another story).

Mine is a "3" pre-pay...

But, for vodafone, here's a couple of pointers..

[http://www.geekology.co.za/blog/2009/05/configuring-vodafone-3g-modem-on-ubuntu-linux-904-jaunty-jackalope/](http://www.geekology.co.za/blog/2009/05/configuring-vodafone-3g-modem-on-ubuntu-linux-904-jaunty-jackalope/)

[http://ubuntuforums.org/showthread.php?t=1305931&page=5](http://ubuntuforums.org/showthread.php?t=1305931&page=5)

There *does* seem a bug reported for vodafone models with 9.10 ... ::sigh::

there is some hope here ...

[http://fostergrant.ubuntuforums.org/showthread.php?p=8551842](http://fostergrant.ubuntuforums.org/showthread.php?p=8551842)

Regards,

Phill.

---

### Post by rodst on 2010-01-01
The Vodafone 3G dongle is from Huawei with driver supplied by them (2.0.3.8x.SP08 ) . These details were extracted from the Windows system. Thanks Phillw for the links. Am reading them now. The problem is that being new to Ubuntu I also have to learn how to run scripts etc. Will persevere.

---

