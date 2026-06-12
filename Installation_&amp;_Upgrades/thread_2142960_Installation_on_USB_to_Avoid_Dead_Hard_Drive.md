---
title: "Installation on USB to Avoid Dead Hard Drive"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by yizrahomme on 2013-05-07
Hi,
I have a Toshiba NB200 on which the hard drive is dead.  The other week, I went camping with my monstruous Toshiba Satellite whatever, and although it was a great use, the weight put me off.

So I considered buying a new hard drive for the little NB200, and then had the 'bright idea' of using a USB version of Linux.  All I want the netbook for is to write a blog, and that can be done in vim, using persistent mode on the USB stick with, say 500 MB reserved for files, right?

I got the i386 ISO of Xubuntu, and used the Universal USB Installer on my office Windows laptop.   Creation of the stick went well, and when I boot the aforementioned work laptop off it, it goes to the Ubuntu Live, with the option of 'trying Ubuntu', or 'installing Ubuntu'.

When I try the same boot on my netbook, I get the blue Ubuntu screen for ages, and when I hit ESC, it reveals 'can't umount /cdrom: device busy'.

But there isn't a CDROM drive on that netbook.

Anyone got an idea as to how I can get it to boot off the stick?

Thanks.

---

### Post by PowerBarry43 on 2013-05-07
Hi.

I'm pretty sure this is a bug with the image you have.

here's an enormous thread on the problem:
[http://ubuntuforums.org/showthread.php?t=1443231&page=18](http://ubuntuforums.org/showthread.php?t=1443231&page=18)

post 176 lists a solution.

From what I read, the gist is this. Download and install ubuntu minimal to the usb stick.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This will be a full install not a liveusb so make sure when installing you put the bootloader on the usb stick too.

Build your image from there starting with.
```

sudo apt-get install ubuntu-desktop
```

Hope this helps!

Barry

---

### Post by yizrahomme on 2013-05-07
> **PowerBarry43 said:**
> Hi.

I'm pretty sure this is a bug with the image you have.

here's an enormous thread on the problem:
[http://ubuntuforums.org/showthread.php?t=1443231&page=18](http://ubuntuforums.org/showthread.php?t=1443231&page=18)

post 176 lists a solution.

From what I read, the gist is this. Download and install ubuntu minimal to the usb stick.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This will be a full install not a liveusb so make sure when installing you put the bootloader on the usb stick too.

Build your image from there starting with.
```

sudo apt-get install ubuntu-desktop
```

Hope this helps!

Barry

Hi there,
Thank you very much for this, I'm about to try your solution.

Just one note: I'm not trying to 'install' the OS to a hard drive, as the hard drive on that netbook is dead.  I want to keep it on the USB stick.

Off to try now ...

---

### Post by yizrahomme on 2013-05-07
> **PowerBarry43 said:**
> Hi.

I'm pretty sure this is a bug with the image you have.

here's an enormous thread on the problem:
[http://ubuntuforums.org/showthread.php?t=1443231&page=18](http://ubuntuforums.org/showthread.php?t=1443231&page=18)

post 176 lists a solution.

From what I read, the gist is this. Download and install ubuntu minimal to the usb stick.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This will be a full install not a liveusb so make sure when installing you put the bootloader on the usb stick too.

Build your image from there starting with.
```

sudo apt-get install ubuntu-desktop
```

Hope this helps!

OK, well I think the problem is with the netbook, rather than with the image or the USB stick.

I just tried with Fedora 18 (or is it 1.8..?), and on the netbook, had a similar error about I/O.  On my office laptop, it booted with no problem.

Too bad.  Looks like the hard drive of the netbook will be getting acquainted with the business end of a Philips screwdriver this evening, before going to the big trash can in the sky.  

Thanks anyway.

---

### Post by yizrahomme on 2013-05-07
Right, well another update.  I got the hard drive compartment open (even though I basically had to rip it off, since I had no screwdriver that would fit), and after removing the hard drive, the image suddenly started to work.  

All I have to do now is duct tape a piece of stiff card over the WLAN adaptor, and I have a working Linux netbook.  :)

---

