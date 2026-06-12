---
title: "Copy disc to usb stick"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by ileti on 2008-01-23
Hello,

I have machine that somebody change the boot up settings. GRUB open from USB stick then load Ubuntu from HD that connecting IDE. I don't know how do it exactly works. I want to boot and use all usage from just usbstick without Harddisc.  

Some details of my computer

In GRUB there is two options 
In first Options - kernel -  
    <l root=/dev/sda1 ...
In Second Options - kernel 
    <l root=/dev/hda1 ...
Other parameters showing "..." options is same both of them.

How to resolve this problem.

Thanks...

---

### Post by jeffus_il on 2008-01-23
Maybe this will help you.
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

---

### Post by ileti on 2008-01-23
Hello,

Thanks, link is realy good but I think I need a little bit different thing. If I copy harddisc to USB stick that including GRUP, My problem is resolved. How to copy entire of disc to USB stick and is it enough just change /dev/hda1 to with /dev/sda1 in GRUB.

Thanks

---

### Post by jeffus_il on 2008-01-23
I am not sure exactly what you are doing, but you have to watch the value of ```
root (hd 0,0)
```
It may change to ```
root  (hd 1,0)
``` depending on your system.

See the mapping file  "device.map" in your grub directory.

---

