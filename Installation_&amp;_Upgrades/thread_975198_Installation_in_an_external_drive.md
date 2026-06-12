---
title: "Installation in an external drive"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by joni.loky on 2008-11-08
So what I would like to do is install Ubuntu in an external USB drive which I'm going to use with my laptop (running Vista :S). The idea is that when the disk is plugged in I'll get the Ubuntu Grub and I'll be able to run Ubuntu, and when the disk is not plugged in then Windows will start normally.

Is this possible? How?

Thnx guys.

---

### Post by sukhhari on 2008-11-08
Hi,

I don't thing so, this will possiable in External HDD, onething you do? make two partitions one Windows Vista other one for install Ubuntu.

:popcorn:

---

### Post by caljohnsmith on 2008-11-08
I think it may be possible if you set your BIOS boot order so that the USB drive comes before the Vista drive. That way the USB drive will boot if it is present, but if not, the BIOS should default to booting your Vista drive. The only problem I can foresee with that is if your BIOS still treats your Vista drive as the second boot drive when it boots it, even if the USB drive is not present; if that happens, Vista may not boot since it will only normally boot from the first boot drive. But I think there is a good possibility it will work, so you have nothing to lose by trying. 

One small caveat though: when you install Ubuntu, in the final stage of installation, be sure to hit the "advanced" button and have Grub installed to /dev/sdb or whichever is your USB drive, and not /dev/sda or (hd0). If you just use the default (hd0), Grub will be installed to the MBR (Master Boot Record) of your Vista drive, which you don't want I assume. :)

---

### Post by joni.loky on 2008-11-08
Thnks guys...that's what I figured.
Now I'm going to put a little twist in the situation :S
My laptop is an HP Pavilion tx2510us.
Great laptop BUT the AMD Turion X2 works at high temperatures and during the Ubuntu instalation it re-boots due to overheating :S

So...
Is it possible to install Ubuntu to an external drive FROM windows. Like I would install a normall software. You know.....with an installer or something.

Another alternative. Is it possible to install Ubuntu to an external drive using another computer and THEN plug it into my laptop and reconfigure it??!?!

Thnx guys....

---

### Post by gali98 on 2008-11-08
No guys, this is totally possible. In Intrepid, there is a program to install Ubuntu onto a usb drive. (System->Administration->Create a Usb startup disk) Just set the bios on the laptop to boot from removable devices, and you should be set.
Kory

Edit: and oh... if you install Intrepid, you shouldn't have the thermal problems....

---

### Post by joni.loky on 2008-11-09
Sooo.....If I install Ubuntu 8.10 to another computer, and then I use that program I should be set?
What about driver configuration?

---

### Post by gali98 on 2008-11-09
That's what Im not sure about... I don't know how it works.... You could also install Ubuntu in a virtual machine, then do the usb thing.....
Kory

---

### Post by joni.loky on 2008-11-09
Yeah installing it in a virtual machine may be a good idea.
Thnx.

---

