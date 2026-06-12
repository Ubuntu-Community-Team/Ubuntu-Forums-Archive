---
title: "netbook remix in an iso ? how to install?"
date: 2009-07-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hallavej on 2009-07-12
I am confused. With jaunty I dd'ed an img-file to a usb-stick, reboot, install, thats it!
With karmic netbook remix is in an iso-file. What do I do with it? A netbook does not have a cd-rom drive. If I dd the iso-file to a usb-stick it does not boot.
How do I install karmic netbook remix?.

---

### Post by jmmL on 2009-07-12
Try using System > Admin > USB Startup Disk Creator

I think that's what you'll need.

---

### Post by ktp on 2009-07-12
you can try using the "USB Startup Disk Creator" which can be found under System -> Administration menu.

There is also following document which might help:

[https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html)

---

### Post by Hallavej on 2009-07-12
thanks.

---

### Post by lesser on 2009-08-12
Okay, but now I have a similar, but somewhat different problem: I have to make a bootable Karmic USB from an .ISO (not .IMG) file. Because i don't have a proper microSD -> USB adapter for my desktop, I have to do this in my WinXP netbook that I want to convert. 

Jaunty is supplied as an .IMG so I could use "Win32 Disk Imager", but for network support, I need Karmic. 

So my question is:
- Is there a IMG of Karmic that I'm overlooking?
- Is there a WinXP tool that can create a bootable USB from an iso file?

Cheers

---

### Post by taavikko on 2009-08-12
> **lesser said:**
> Is there a WinXP tool that can create a bootable USB from an iso file?

Cheers

unetbootin. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by andrewsomething on 2009-08-12
When you say "for network support" do you mean wireless or networking all together? If just wireless, as you already seem comfortable with the IMG image, just install Jaunty and upgrade with "update-manager -d" while wired.

To create a bootable usb stick from windows, check out UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

As fars as an IMG for Karmic, I believe the final release will have one but that they don't role them fore alphas, ect...

---

### Post by lesser on 2009-08-12
Great! Thanks for the quick replies. Indeed my major concern was the wireless. My netbook is a Eee 1008HA and I've read that 9.10 runs a lot better than 9.04. 

But thanks to you I have to options to try.

---

### Post by lesser on 2009-08-12
Got it running now. The Karmic ISO wouldn't boot. The daily live cd (that you can download from within unetbootin) did boot okay. Thanks again for your help.

---

