---
title: "lg x130 netbook cannot start from usb with xubuntu"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by revolct on 2010-12-21
sup everyone who read this
going to install xubuntu on my shitbook but no way.
It cannot start from usb. But usb works, 100% cuz I've installed win7 this way before.
So, how to install xubuntu?
(btw ive tried ubuntu too - the same ***** does not start,:popcorn: suko)

---

### Post by sikander3786 on 2010-12-21
Welcome to the forums :-)

How was the USB drive prepared? Did you check the MD5SUM of the image before burning it to USB?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Are you sure the boot order in Bios is properly set to boot from USB drive?

> going to install xubuntu on my shitbook but no way.
It cannot start from usb

What happens then? Any error messages? Blank screen? Or your computer just ignores the USB drive and boots straight in to the other OS?

---

### Post by revolct on 2010-12-21
> **sikander3786 said:**
> Welcome to the forums :-)

How was the USB drive prepared? Did you check the MD5SUM of the image before burning it to USB?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Are you sure the boot order in Bios is properly set to boot from USB drive?



What happens then? Any error messages? Blank screen? Or your computer just ignores the USB drive and boots straight in to the other OS?

Yeah... md5 is ok, I've used [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/), not bootin, but it doe not matter I think. I sure, usb boot was chosen first of course, I'm not totally lame )

There are no errors, nothing but the main screen with "Press F2 for BIOS, F10 for multyboot". But it doesn't work, nothing but POWER button :(
 I think its somewhat about xubuntu cannot work with this peace of sh..t.

---

### Post by sikander3786 on 2010-12-21
I would still recommend to use Unetbootin as some problems have been reported previously with syslinux file names when using pendrivelinux.

And it would also be handy to know your hardware specs.

---

### Post by revolct on 2010-12-21
> **sikander3786 said:**
> I would still recommend to use Unetbootin as some problems have been reported previously with syslinux file names when using pendrivelinux.

And it would also be handy to know your hardware specs.

Thx for your help, but it still does not work, even with Unetbootin.
[http://www.pcmag-mideast.com/2010/01/31/lg-x130-review/](http://www.pcmag-mideast.com/2010/01/31/lg-x130-review/) this is my book

---

### Post by sikander3786 on 2010-12-22
> "Press F2 for BIOS, F10 for multyboot". But it doesn't work,

By pressing F10, can you gain access to the boot menu and select your USB drive?

---

### Post by revolct on 2010-12-22
> **sikander3786 said:**
> By pressing F10, can you gain access to the boot menu and select your USB drive?
Nope, this menu is frozen when usb with linux is plugged in.
but usbstick itself works, 100%.

---

### Post by sikander3786 on 2010-12-22
> **revolct said:**
> Nope, this menu is frozen when usb with linux is plugged in.
but usbstick itself works, 100%.
I can't say much on that but seems like your Bios doesn't like your USB drive. If you have another USB drive, try that.

Or look for a Bios upgrade and if available, upgrade your Bios and try again.

---

### Post by revolct on 2010-12-22
> **sikander3786 said:**
> I can't say much on that but seems like your Bios doesn't like your USB drive. If you have another USB drive, try that.

Or look for a Bios upgrade and if available, upgrade your Bios and try again.

BIOS is already updated, it was my first thought.
btw, I've installed win7 before with this usb on this netbook. It does not work only with linux =\
UPD The problem was indeed in my usbstick. I've tried with another, it was ok.
wtf, what's wrong with my flash?

---

### Post by sikander3786 on 2010-12-22
> UPD The problem was indeed in my usbstick. I've tried with another, it was ok.

That was my initial thought. Glad that you figured the problem but sad that you had a hardware loss :-(

If satisfied, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

