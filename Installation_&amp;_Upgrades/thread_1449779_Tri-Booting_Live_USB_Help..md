---
title: "Tri-Booting Live USB Help."
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Dj TweeX on 2010-04-08
I suppose this is a good place to put this.
i am looking to make a Tri-Boot live USB with Linux Mint, Fedora and Ubuntu.
Now, so far it seems slightly straight foreward. but, how would i go about making grub see all of the OS's. and do any of you believe there are any drawbacks? 
I will have more questions as my project continues, so please stick with me!
thank you!!
Gabe R.

---

### Post by Kellemora on 2010-04-08
Hi TJ

Live USB is above my head!

But dual, triple or even quad booting is no problem for Grub!

I have an OLDE eMach4165 quad booting Ubuntu, Debian, CentOS and WinDOZE!
Albeit, it hasn't been moved off Ubuntu in over a year, hi hi........
Most of our other machines are triple boot, for no other reason than we could do it, and had LARGE wasted hard drives in them.

I didn't make it so don't know how it was done, but I have a DVD that contains Knoppix, Ubuntu LIVE, Super Grub and one of the GParted programs, all require they be booted into.  Grub comes up and I select which one I want and Press the 'ANY' key, and away it goes!

The 'ANY' key is located just under the big red 'PANIC' key!
Just kiddin'!  The 'ANY' key on my keyboard has the word 'ENTER' written on it!

TTUL
Gary

---

### Post by oldfred on 2010-04-08
I saved some links. Some more useful than others.

I used the boot from ISO -panticz to keep space at a minimum but then they are not full installs.

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
-----------------
[http://www.knoppix.net/wiki/USB_Based_FAQ](http://www.knoppix.net/wiki/USB_Based_FAQ)

[http://forums.fedoraforum.org/showthread.php?t=217113](http://forums.fedoraforum.org/showthread.php?t=217113)

---

### Post by Dj TweeX on 2010-05-31
Sorry for the delay.

i should be specific.

i would like 4 partitions.

the first containing just GRUB

the second third and forth containing different linux distros.

how would i go about setting this up??

---

### Post by C.S.Cameron on 2010-06-01
You should be able to create the partitions using gparted, disable your internal HDD, plug in your flashdrive, boot the Live CD from each of the distros and install to the appropriate partition.
grub should be able to find the preceding installs automatically.

---

