---
title: "Install Ubuntu / USB Pendrive"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by delta99 on 2008-10-17
Hi there, I've tried to follow many guides without much success.

I've managed to get into the livecd mode, but couldnt install it on the usb drive. (i followed this guide: [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar))

The laptop is a thin client with a 500mb ram. I want to run ubuntu on it or (kubuntu) with a 4gb peak3 usb drive.

Can you please provide the steps on how to install ubuntu from the usb drive and to install the os onto the same usb drive. (should i partition it first?)

please help

---

### Post by Pumalite on 2008-10-17
Try this:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by C.S.Cameron on 2008-10-17
If you want a full install, I agree with Herman.
If you prefer a persistent Live CD image, a quick and simple method is:

Boot 8.10 Live CD.
In terminal type: 'sudo apt-get install usb-creator'.
After installation, insert flash drive and type: 'usb-creator'
You can chose persistence or not.
Within 4 minutes your bootable thumb drive should be ready.

I prefer the full install myself, however it takes a 4G drive and the persistent, (disk image), install will fit on a 1G.

---

### Post by delta99 on 2008-10-18
Thanks for the help,

I've just setup the stick again (from the link i posted).

And just booted it, got to the ubuntu setup screen and selected "run or install", black screen now for 20 mins...

So how do I actually prepare the usb disk? I have no cd drives. I need to run the install from the usb drive and also install ubuntu on the same disk.

please help

there is too many guides, been trying for 3 days now

---

### Post by delta99 on 2008-10-18
Basically

How do I do this: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/)

WITHOUT a cdrom

thanks alot
actually NOT via windows too, :D

---

### Post by C.S.Cameron on 2008-10-18
Unetbootin will build a (non persistent) Flash drive from an ubuntu iso in windows.
This flash drive is a Live CD image, it can be used to install a full version of ubuntu to a second flash drive just like the Live CD.

---

### Post by zakalwe_ukuk on 2008-10-18
Anyone know if its still the case with the latest release that if you install via usb then using usb drives is problematic on the system afterwards?

---

### Post by Pumalite on 2008-10-18
I have a Hardy and an Intrepid installed in 8 GB pendrives with Herman's method and they have never been a problem.

---

### Post by zakalwe_ukuk on 2008-10-18
No i meant if you install to  a normal hd with the live cd on a usb stick. It tends to confuse the os and it wont let you mount usb drives without jumping through hoops. Just wondering if they've fixed it yet.

---

### Post by speed32219 on 2008-10-18
Not trying to Hijack the thread, just have a quick question and C.S. Cameron has a few posts on Unetbootin.  What would be the best way to install intrepid 8.10 on a bootable 4 GB flash drive? (Donwload 8.10 ISO to HD and then do a full isntall to a 4 GB flash?) I want to strip it down to the bare essentails (Intrepid) for my install/Hardware but I would like to setup 2-4 GB of swap space on a internal HD.  Can this be done?  

I now have Hardy and want to boot to intrepid using my new mobo combo that is currently working with 8.04 with some issues (Installed PCI devices to overcome driver issues) that are to be corrected in  8.10.  My MB is an intel DG45ID G45 Northbridge, ICH10R Southbrige and Intel 82567LF Ethernet port.  SO I want to boot from flash rather than a dual boot scenerio.

---

### Post by jasonruk on 2009-03-06
Hi there.

My my friend and I tried something similar but adding the complete OS onto a usb stick, we tried it several different ways and have a post on my blog site that shows how we got it to work.

Hope it's of use.

[http://december1975.wordpress.com/2009/03/01/ubuntu-810-usb-stick-installation](http://december1975.wordpress.com/2009/03/01/ubuntu-810-usb-stick-installation)

Jason

---

