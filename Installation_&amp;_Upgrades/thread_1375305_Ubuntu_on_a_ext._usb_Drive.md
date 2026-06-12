---
title: "Ubuntu on a ext. usb Drive"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by PaulNL on 2010-01-07
Hello all

I have a laptop (Acer 3650) and i have a strange problem. When i use a live version from Ubuntu 9.10 on a USB flash it works perfect. When i install it on my laptop it installl all but it won't start. I have to tel my IDE is broken so i use a ext HD on USB can it be that that is the problem ???

On the live all works Sound, Keybord WiFi 


Can someone tell me if thare is a sollution for it.

Sorry for the bad EN 

Paul

---

### Post by darkod on 2010-01-07
By default the grub2 bootloader can install itself on the internal hdd even if you are installing ubuntu on the ext hdd. And even if the int hdd is broken, as long as it's there.
Make sure you have grub2 on the ext hdd and you are booting that drive. Check in BIOS to confirm that the ext hdd is first in boot order, the USB device needs to be first before CD, int HDD, etc.

Try that first and if it still doesn't work there is a script you can run so we can see your boot process in detail and help.

---

### Post by kansasnoob on 2010-01-07
I'm not sure I quite understand but is this helpful:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by PaulNL on 2010-01-08
the question is now how do i get it work with a external usb HD. The problem is installation goes ok but after installing the screen freeze on the startup. on the screen is onley Boot written.

The bootorder is set to USB HD i don't have a CD or something like it in the machine

How o i make it work ???


Paul

---

