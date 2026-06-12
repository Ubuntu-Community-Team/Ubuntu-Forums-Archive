---
title: "Loading screen stuck."
date: 2016-09-01
forum: Installation &amp; Upgrades
---

### Post by gingo3 on 2016-09-01
Hi,

I have a problem when I try to install Ubuntu 16.04.1 64 bit for a dual boot.
I will tell you what I did and what is happening.

1. Download Ubuntu iso and burned it to an usb.
2. Booted from usb.
3. Selected "Try Ubuntu without installing".
4. I get the Ubuntu logo with the dots and then it gets stuck.

The logo is always stuck when the first dot is white.
I also tried installing XUbuntu and it also got stuck when it loaded at the same moment every time.

My specs:
```
Operating System
    Windows 10 Home 64-bit
CPU
    Intel Core i7 6700HQ @ 2.60GHz  44 °C
    Skylake 14nm Technology
RAM
    16.0GB
Motherboard
    ASUSTeK COMPUTER INC. GL552VW (U3E1)
Graphics
    Generic PnP Monitor (1920x1080@60Hz)
    Intel HD Graphics 530 (ASUStek Computer Inc)
    4095MB NVIDIA GeForce GTX 960M (ASUStek Computer Inc)   50 °C
    ForceWare version: 372.54
    SLI Disabled

```

I hope this problem can be solved, and if I need to provide more information I will do.
Thanks in advance!

---

### Post by Bucky Ball on 2016-09-01
Welcome. Try this. When you get to the purple screen with the icon down the bottom after boot, think you can hit any key there and should take you to the options screen where you have selections along the bottom. Hit F6 and some options should pop up. Choose 'nomodeset' and proceed to 'Try Ubuntu'.

I may have gotten the route there slightly mixed up as haven't done this in awhile, and someone else might be able to clarify, but the main thing is you want to try the 'nomodeset' option selected from the pop-up menu from F6.

If that works to get you to a desktop then we can make the option permanent in a hard drive install (any changes you make in 'Try Ubuntu' will be lost on reboot).

---

### Post by gingo3 on 2016-09-01
Hi, thanks a lot for your reply I tapping f6  and I saw this log no option menu or something.

[IMG]http://i.stack.imgur.com/ugP3w.jpg[/IMG]

---

### Post by ajgreeny on 2016-09-01
I think you are pressing F6 too late if you do not see the boot options page, but I also suspect your machine with Win 10 is UEFI and that you may be booting the USB in legacy mode.

If your computer has a key to press to choose the boot device (F8, F11?) make sure you choose the USB device name that starts UEFI and you may get a bit further.

---

### Post by gingo3 on 2016-09-01
Thanks a lot for your help but I managed to fix this problem by adding "nomodeset" to the linux line when pressing e in grub.

---

### Post by ajgreeny on 2016-09-01
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by Bucky Ball on 2016-09-01
> **ajgreeny said:**
> Great! Please mark as SOLVED from the Thread Tools menu up-top.

See the link in my signature if you don't know how. Good news and enjoy the forums and OS. :)

---

