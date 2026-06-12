---
title: "Install to external harddrive, that is to be mounted internally on another machine"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by trashjunkid on 2008-08-10
Sorry for the longish post title.

I have an old system (pent 3 500, 15 gb harddrive, 384mb ram). I am interested in making it into a server for our home (I know it is old- but if I have some luck here, I will probably get some newer hardware and start over).

Whenever I try to run the live cd for ubuntu or xubuntu (8.04.1) I get booted to the initramfs- and if I don't, then I just get a whole bunch of cd read errors.


Using my newish laptop and armed with an external usb cable from the 15gb hard drive, I want to install from the live disk to that 15gb harddrive by way of the usb connection.

Using the laptop (under Vista) I have hooked up the hardrive to the laptop in that manner, and have wiped/reformatted the drive as fat32.


I am prepared now to boot my laptop up using the live cd (xubuntu) and would choose 15gb usb mounted drive as the drive to install to.

Then I'll put the 15gb hard drive back in the old tower.

The problems as I see them, for starters anyway, are:

Cruising the forum, I have learned that the way grub is loaded and the menu.lst file are the first stumbling steps.

Grub will install to my laptop's harddrive- so how do I force it to get installed to the 15gb usb mounted drive?

If I do get that accomplished, how will I get the the grub to shift from treating the 15gb harddrive as a usb mounted device to treating it as a internally mounted hard drive?

Anyway, that's where I am at the moment. I want to get xubuntu installed to that os-free fat32 mounted as usb drive but going to live it's life as internally mounted 15gb harddrive- and I would be very grateful for all advice and insight.

I am, of course, a complete noob.

-Trashjunkid

---

### Post by trashjunkid on 2008-08-11
(know it's lame to reply to yourself, but ah well)-

Is it possible to copy the necessary files to the harddrive and the command line install?

Again, I can attach the harddrive to a laptop (running vista off harddrive, and has a liveusb fedora 9 system too).

So... can I format/partition the harddrive, copy the right setup files to the harddrive and then boot using a floppy, switch to the harddrive and initiate the install?

Any help is greatly appreciated.

-Trashjunkid

---

### Post by Shazaam on 2008-08-11
Is this what you are looking for? (unetbootin)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by trashjunkid on 2008-08-25
You know I glossed over that option as I was having difficulty getting the ethernet working, but I have done so since then. This sounds perfect and I will try it soon. Thanks for the tip,
Trashjunkid

---

