---
title: "New Ubuntu 16.04 intall, no mouse, keyboard, network adapters"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by bgiannes on 2016-05-04
So i did a new install of Ubuntu 16.04 to a new SSD, no USB mouse, keyboard, network adapters.  i did try to reinstall again but got the same result.

System has a ASUS P5Q turbo, 8Gb Ram...  Note i can boot to my old install 14.04 without issue.  Also the install completes without errors.

I did find my old PS/2 keyboard so i can get the terminal.

It would seem that no USB input drivers have loaded, or any network adapters, both lsusb, and lspci do show the devices are there.

Also i notice that kernel 4.4.0-21 in grub however uname -a shows some old kernel loaded?


please help...

---

### Post by bgiannes on 2016-05-07
Well i got this one fixed myself.


i found the next proposed kernel and downloaded, (on the 14.04 boot) 

linux-headers-4.4.0-22-generic_4.4.0-22.38_amd64.deb
linux-image-4.4.0-22-generic_4.4.0-22.38_amd64.deb

then copy the files to the 16.04 SSD, and installed them with

dpkg -i lin*.deb

did a update-grub and rebooted.

this got me back one of the network adaptors, from there i could config it and do a update, upgrade then reboot.

---

