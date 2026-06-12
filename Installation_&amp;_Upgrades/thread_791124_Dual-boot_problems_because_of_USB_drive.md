---
title: "Dual-boot problems because of USB drive"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by JamesBrausch on 2008-05-11
I blew it.

I have a laptop running Vista.  I decided to install Ubuntu to a USB thumb drive.

It works.  I can boot to Ubuntu by putting my USB drive as the first bootable device.

I can also put my hard drive back to the first bootable device and I get a boot menu allowing me to choose Vista or Ubuntu.

However, if I remove the USB drive (which I really don't want to always have to carry just to use my laptap with Vista now), I have a major problem.

I can no longer boot to Vista.  The dual boot sector tries to load grub from the non-existant USB drive and gives a General error #21.

How can I put my system back the way it was.  I just want to boot into Vista with no boot menus and no USB drive plugged in.

My next attempt will probably be to try to install Ubuntu to my hard drive as a Windows app.  But I need to get my system back working without the thumb drive around first.

How can I fix that boot sector to make it a normal Vista boot sector again?

Thanks in advance.

This is Ubuntu 8.04.

-James D. Brausch

---

### Post by meierfra. on 2008-05-11
I wrote a howto for this situation:

[http://ubuntuforums.org/showthread.php?p=3995006#post3995006]("http://ubuntuforums.org/showthread.php?p=3995006#post3995006")

There is a small problem with the howto:  "ms-sys" is not in the 8.04 repositories. You can get "ms-sys" from
[URL="http://packages.debian.org/etch/ms-sys"]
http://packages.debian.org/etch/ms-sys[/URL]
or your can use the other methods indicated in the howto to restore the MBR of your internal drive.

---

