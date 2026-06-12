---
title: "Install off USB stick from Windows??"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Zurtex on 2008-02-06
I really need to use my USB stick like a Live CD, I've found several guides but they all assume 1 of 2 things:

* I have a running copy of Linux

* I can burn my own LiveCD

Neither of these I have or can do, I need to be able to do everything off Windows, any help please?

---

### Post by markitect on 2008-02-06
Check out:
[http://www.howudune.com/2007/04/how-to-boot-knoppix-40-from-a-usb-flash-drive/](http://www.howudune.com/2007/04/how-to-boot-knoppix-40-from-a-usb-flash-drive/)
The direction should work for any Linux distro, just replace knoppix cd image with ubuntu cd image.

---

### Post by Zurtex on 2008-02-06
> **markitect said:**
> Check out:
[http://www.howudune.com/2007/04/how-to-boot-knoppix-40-from-a-usb-flash-drive/](http://www.howudune.com/2007/04/how-to-boot-knoppix-40-from-a-usb-flash-drive/)
The direction should work for any Linux distro, just replace knoppix cd image with ubuntu cd image.
Trying it out now, but nothing seems to happen when I run the command:

"&#8220;C:\syslinux-3.61\win32\syslinux.exe F:&#8221;

Should I be able to see any difference?

Edit: I assume isolinux in the ubuntu installation is the same as bootisolinux in these instructions?

---

### Post by Zurtex on 2008-02-06
Thanks so much, worked it out and solved it, I love ubuntu when I get it working :)

---

### Post by berget on 2008-02-07
I have the same issue as mr. Zurtex above - but I can't get it to work.

I follow the steps, boot from the USB, but get an error message saying that it can't load the operating system. Any ideas? It is a different error message than from loading from a blank USB stick, so there's got to be something halfway correct there.

I tried both Syslinux 3.60 and 3.61 (latest release).

Thanks for any help!

---

### Post by Zurtex on 2008-02-07
My error that originally came up was something like "Can not find boot table" or something like that.

The only thing I can suggest is to make sure you followed all the instructions about changing the files around and re-naming them, also as per the comments below I also added '-sma' on to the command line to make it:

“C:\syslinux-3.61\win32\syslinux.exe F: -sma”

---

