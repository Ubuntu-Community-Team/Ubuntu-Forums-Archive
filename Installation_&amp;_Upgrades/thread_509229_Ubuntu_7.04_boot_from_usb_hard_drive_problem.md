---
title: "Ubuntu 7.04 boot from usb hard drive problem"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by zenit123 on 2007-07-25
Hi

I am new to Ubuntu and having problems booting it up from a USB external hard drive. I have booted the computer using the Live CD and have installed Ubuntu 7.04 onto a new USB external hard drive. All partitioning and installing in the new external hard drive has gone smoothly but ubuntu does not boot up from the usb external hard drive. It boots into windows which is on the internal hard drive and lower down in the bios boot order.

I have changed the settings in the bios and the bios does check the usb external hard drive for booting but for some reason does not continue to boot and boots into windows.

Is there any thing I should be doing or am missing.

thanks ahead

---

### Post by jaywalker13 on 2007-07-25
Don't know if this is the same thing, but I had that problem when using an external HDD. If I let it boot into XP, then checked that the external HDD was recognised by XP and rebooted without turning off the external HDD, it would reboot into Ubuntu.

Messy, so just 2 days ago I gave up and learned how to partition the HDD and set up Ubuntu on that.

Jay

---

### Post by confused57 on 2007-07-25
I would recommend burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You can also use the Ubuntu live cd to install grub's IPL to the external hard drive's mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

For example if "find /boot/grub/stage1" returns "root (hd1,0)", you would enter:
```
root (hd1,0)
setup (hd1)
```

If you get a grub menu, but Ubuntu still doesn't boot...highlight your Ubuntu entry, press "e", then change root from (hdx,y) to (hd0,y), then press "b" to boot...y meaning leave this value as it is.

---

