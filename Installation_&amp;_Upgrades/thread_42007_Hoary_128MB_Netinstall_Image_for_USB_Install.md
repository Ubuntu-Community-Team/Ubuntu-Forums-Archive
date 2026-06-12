---
title: "Hoary 128MB Netinstall Image for USB Install"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by ajslater on 2005-06-15
[Hoary 128MB Net Install Image for USB install](http://aj.daisho.us/ubuntu/) 

I made a 128MB vfat network install image for Ubuntu by replacing 3 files in the Debian one.

Works great from a usb drive. If your USB drive is mounted as /dev/sda:

  $ bzcat hoary.img.bz2 > /dev/sda
  

And viola! A superfloppy style usb key installer on your small usb key. I made this to install Ubuntu on my new IBM X series laptop that came without a CD Drive.

---

