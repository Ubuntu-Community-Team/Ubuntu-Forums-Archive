---
title: "Unable to boot from usb"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by s.v.z on 2010-10-11
I`m trying to get a fresh install of Ubuntu 10.10. I`ve used unetbootin to write the image to a usb flash, but every time I try to boot from it I just get the burg splash screen. I`ve changed the boot order in bios and so on, but it starts burg all the time. The image md5 is also right.

---

### Post by BingHeZhouKe on 2010-10-11
are you sure the  usb flash is bootable? get another pc to test if the usb flash is a bootable one.

---

### Post by s.v.z on 2010-10-11
Yes, it is bootable. Just can't boot on my laptop.

---

### Post by efflandt on 2010-10-11
I have never used unetbootin, but something changed in the syslinux used by the Startup Disk Creator for 10.10.  And it looks like unetbootin might not support that yet unless you have the proper unetbootin version.  In a web search for "ubuntu 10.10 boot iso usb", one of the things that came up about unetbootin said:

***[I]Note to Ubuntu 10.04 users installing 10.10: The version of  UNetbootin from Ubuntu's repositories is outdated and doesn't support  Ubuntu 10.10. An [update is pending]("http://bugs.launchpad.net/unetbootin/+bug/615285") but in the meantime please use the current version from this website or the [PPA]("http://launchpad.net/%7Egezakovacs/+archive/ppa") (which does support Ubuntu 10.10)*[/I]**

I created a 64-bit bootable 10.10 release iso on USB flash that works fine.  But I used **Startup Disk Creator** to create that from a regular installation of 10.10 beta on a USB hard drive, updated to RC, updated to what appears to be the release version.  But maybe Startup Disk Creator in 10.04 has been updated to handle, because the Ubuntu website does not mention which Ubuntu version you have to use for Startup Disk Creator in its "Show Me How" to create 10.10 bootable iso on USB.

PS: Even if you set USB first in boot order in BIOS for some computers you might still need to press a key during the BIOS splash screen to select boot device.  I know that I need to do that on Dell computers.

---

### Post by s.v.z on 2010-10-11
The problem is that it DOES boot on another pc, but won`t do it on my laptop. I`ve got an hp6735b.
I`ve already tried the unetbootin from ppa. I`ve selected the boot from usb hdd manually. Still the same.. Will try to boot from an SD card(O_o) now.

---

### Post by s.v.z on 2010-10-11
Well, I`ve just installed it from an SD card. Works fine. It can even fade the screen! =)

---

