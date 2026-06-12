---
title: "Installing Ubuntu on an external hard drive"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by mutew on 2008-09-16
My Win XP/Ubuntu dual boot system on my laptop got effed a couple of days ago due to problems with the Ubuntu install. This took down GRUB with it too since /boot was on the same partition as the Ubuntu install. Due to this I can no longer boot into Windows and to further complicate matters my DVD drive refuses to read any bootable disc I put into it. 

I tried a net-install but that kept failing on me due to a pathetically slow connection. The only way out seems to be to remove the laptop hard disk and connect it as a USB-drive to my computer and perform the install from the computer. My question is will this hard disk function correctly on the laptop once it is plugged back in? I am hoping that drivers and configurations do not cause any issues later. Has anyone tried this? If yes, what was the outcome?

---

### Post by meindian523 on 2008-09-16
Erm,how exactly would you convert the laptop internal HDD into an external,pluggable USB HDD?

Assuming you did that,there won't be any problems with drivers,because GNU/Linux loads modules dynamically every startup depending on the hardware it detects,that's how you can have a USB portable pendrive linux[pendrivelinux.com].

As to whether the disk will function correctly,I really can't comment.

---

### Post by prshah on 2008-09-16
> **meindian523 said:**
> Erm,how exactly would you convert the laptop internal HDD into an external,pluggable USB HDD?


It quite easy; look up "USB enclosure" in Google.

> **mutew said:**
> The only way out seems to be to remove the laptop hard disk and connect it as a USB-drive to my computer and perform the install from the computer. My question is will this hard disk function correctly on the laptop once it is plugged back in?


Yes, you can do this. However, you (may) need to change GRUB settings to get your HDD to boot in your laptop. For this you will need to learn a little bit about the GRUB command line. It's very simple, though.. and there are a number of guides available; I'll post a good one shortly.

Another thing I'd suggest it to boot off a pendrive and install Ubuntu. There are a number of guides on how to transfer a live CD to a USB pendrive at [www.pendrivelinux.com](www.pendrivelinux.com)

---

### Post by mutew on 2008-09-16
> **prshah said:**
> 
Yes, you can do this. However, you (may) need to change GRUB settings to get your HDD to boot in your laptop. For this you will need to learn a little bit about the GRUB command line. It's very simple, though.. and there are a number of guides available; I'll post a good one shortly.


By this I presume you mean that the hd device label will have to be changed.

> **prshah said:**
> 
Another thing I'd suggest it to boot off a pendrive and install Ubuntu. There are a number of guides on how to transfer a live CD to a USB pendrive at [www.pendrivelinux.com](www.pendrivelinux.com)

Booting off a pendrive isn't an option since the laptop only supports netinstall / CDROM boot.

---

### Post by prshah on 2008-09-16
> **mutew said:**
> By this I presume you mean that the hd device label will have to be changed.


You presume right.

---

### Post by caljohnsmith on 2008-09-16
Mutew, I think your idea of plugging your HDD into another computer and installing Ubuntu will probably work fine, but one important point is to make sure that Grub gets installed to the correct HDD master boot record (MBR). Before you run the Ubuntu installer, do:
```
sudo fdisk -lu
```
Figure out which /dev/sdX is your HDD for Ubuntu. Then when you install Ubuntu to that drive, in the last stage of installation, click the "advanced" button, and tell Grub to install to /dev/sdX (whichever is your Ubuntu HDD) instead of the default (hd0). That will ensure that Grub gets installed to the correct HDD. Let me know how it goes.

---

### Post by mutew on 2008-09-16
> **caljohnsmith said:**
> Mutew, I think your idea of plugging your HDD into another computer and installing Ubuntu will probably work fine, but one important point is to make sure that Grub gets installed to the correct HDD master boot record (MBR).
Thanks for the tip, I knew that I was forgetting something important regarding the boot process and this was it. My next post is going to be from the Ubuntu system so you'll know very soon how successfully everything went.

---

### Post by C.S.Cameron on 2008-09-16
Installing to a 2.5" HDD located in an external USB enclosure works fine for me. 
Install just as you would to internal HDD.
USB read / write speed is not as fast as SATA but does not slow normal operations much if you have lots of RAM.

---

### Post by meindian523 on 2008-09-17
And you can learn Grub commandline at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

