---
title: "Ubuntu 8.10 boot install failure. Need help!"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by mu:te on 2008-11-24
I've installed Linux so many times, on some many computers, including my own, but all out of sudden I got this fantastic error when I'm trying to install Ubuntu 8.10.

After booting from CD and pressing "Install Ubuntu" I'm directed to some "Busybox" screen and this error message is shown repeatedly, over and over again..

It sounds something like this.

(initramfs)
(initramfs)
(initramfs)
(initramfs) Bla Bla Bla Hardware Error [Yes]
I/O error, dev sr0, sector 1431176
Buffer I/O error on device sr0, logical block 178897

Howto fix this? My hardware cannot be the problem, Ubuntu been on this computer two-thousandths times..

And FYI. I've burned 3cds, 4x, 8x, 24x, I've tried "all_generic_ide" and "all_generic_ide noacpi nodma noapic nolapic", doesn't work..

- Intel Dual Core 6420 2.13Ghz
- 2GB of mem @ 800mhz
- nVidia 8800
nuff said..

---

### Post by ITAndrew on 2008-11-24
I have encountered the same problem before and it ended up being a bad DVD drive. If you can, try to make a bootable pen drive by copying the ISO to the pen drive, booting up a live CD on a PC you know that works or a PC already running Ubuntu 8.10. Copy the ISO to the desktop of the live OS or Ubuntu install.

Now I am not 100% sure what the application launcer is (to creat bootable pen drive) but I know it is located in the System > Argh drawing a blank. Its there trust me.

Good spot for more info including the location of my brain fart above:
[http://reddevil62-techhead.blogspot.com/2008/11/installing-ubuntu-810-to-usb-flash.html](http://reddevil62-techhead.blogspot.com/2008/11/installing-ubuntu-810-to-usb-flash.html)

After creating the bootable pen drive, try disconnecting the ROM drive and try booting using the pen drive. If this does not work, try swapping your ROM drive for a different known working drive.

---

### Post by mu:te on 2008-11-24
> **ITAndrew said:**
> I have encountered the same problem before and it ended up being a bad DVD drive. If you can, try to make a bootable pen drive by copying the ISO to the pen drive, booting up a live CD on a PC you know that works or a PC already running Ubuntu 8.10. Copy the ISO to the desktop of the live OS or Ubuntu install.

Now I am not 100% sure what the application launcer is (to creat bootable pen drive) but I know it is located in the System > Argh drawing a blank. Its there trust me.

Good spot for more info including the location of my brain fart above:
[http://reddevil62-techhead.blogspot.com/2008/11/installing-ubuntu-810-to-usb-flash.html](http://reddevil62-techhead.blogspot.com/2008/11/installing-ubuntu-810-to-usb-flash.html)

After creating the bootable pen drive, try disconnecting the ROM drive and try booting using the pen drive. If this does not work, try swapping your ROM drive for a different known working drive.

Can you perhaps give me a better details how to do this? Step by step cause I dont seem to be doing this at all..

---

### Post by mu:te on 2008-11-24
This is so ****** typical! God how ****** pissed off i am right now! 

The ****** disk works perfect, but of course i cannot get to the "live" version of the disk, probably because my cd-rom is ******..

Thats great so i decided to try my brothers computer, threw the disk in, and wollah, it works perfect, on the other hand when i plugged my 8gb usb pen, i realized that the pen was ******.. Malfunction in device, ****** great.

So obviously i'm not suppose to be able to install linux on my fuuckin computer, fuuuckin brilliant!!!!

Ps. No i dont give a flying **** about my writing, if you dont like it, **** you.

---

### Post by mu:te on 2008-11-24
All out of sudden my usb pen decided it was a good time to start working and I managed to put the installation on the pen. Now, I've changed the boot to boot from usb but it doesnt..

---

### Post by linux_tech on 2008-11-24
First download Ubuntu 8.10 ISO and then burn the iso to a CD
Next, restart and boot from the Live CD you just made.

Plug in a 2GB or larger USB flash drive.

Start a terminal and type this:
```
wget pendrivelinux.com/downloads/u810/u810.sh
chmod +x u810.sh && sh u810.sh
```

After the install to the flash drive reboot the pc and change the Bios to boot from the USB device.

---

