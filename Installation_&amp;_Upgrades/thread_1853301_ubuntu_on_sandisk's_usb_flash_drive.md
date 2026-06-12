---
title: "ubuntu on sandisk's usb flash drive?"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-10-02
Has anyone installed ubuntu on SanDisk's USB flash drive?

---

### Post by Quackers on 2011-10-02
I haven't done it, but it shouldn't be a problem.
What you would need to do is make sure that grub is also installed to that flash drive - NOT to your main system.

---

### Post by Matrix01 on 2011-10-02
i used sandisk's usb flash drive,

and installled unetbootin with iso files...
[url]http://mirror.yellowfiber.net/ubuntu/11.04/ubuntu-11.04-desktop-
i386.iso[/url]
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
changed boot order, usb floppy in the first, on this HP Mini netbook,

and...used U3 removal tool which is recommended by ubuntu community...
[http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

they did not work.

---

### Post by Quackers on 2011-10-02
USB floppy is for a floppy drive! 
You will need to select something like USB flash drive or maybe even USB HDD as first boot device.
If your bios recognises your flash drive as a HDD rather than a flash drive (like mine does) you may need to first enable external boot devices in the bios too.

---

### Post by Matrix01 on 2011-10-04
this HP Mini has boot order like this;

usb diskette on key / usb hard disk.  Is this the one to set boot order in the first?

usb floppy.

usb cd / dvd rom drive.

notebook hard drive.

---

### Post by Hakunka-Matata on 2011-10-04
> **Matrix01 said:**
> this HP Mini has boot order like this;

[COLOR=Red]usb diskette on key / usb hard disk.  Is this the one to set boot order in the first?
[/COLOR] 
usb floppy.

usb cd / dvd rom drive.

notebook hard drive.
[COLOR=Red]Yes, that looks like the proper one.[/COLOR]

---

### Post by nariub on 2011-10-04
I have done this with 10.04, 10.10, and recently 11.04
pull all the other harddrives, boot the install CD, use the try Ubuntu option (you will see why in a minute)
plug in USB
wait until it is recognized
hit the desktop install icon and install to the USB

I use no swap for the install
after she is done.  DO NOT REBOOT yet.
..
use your favorite editor to edit the /etc/fstab
create tmpfs entries for /tmp and stuff

reboot
remove CD and boot from the stick
instant ubuntu on a stick.  not the live type, a real ubuntu installation.
I suggest an 8G or better, a 4G will get crowded quickly.

---

### Post by Matrix01 on 2011-10-07
so....
do i need CD drive?

this HP mini netbook does not have one.

---

