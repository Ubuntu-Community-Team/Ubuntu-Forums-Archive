---
title: "GRUB2 cannot boot"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Westie. on 2011-01-15
Sorry for the question that everyone else has asked at least once, but I have spent roughly about err, five hours at the least trying to sort this out.

GRUB2 won't boot. It hangs just after the 'Boot from CD' thing in my BIOS.

I've had 1.97 working on my PC about 24 hours ago, but I decided to start afresh and go for Xubuntu 10.10.

I'll post the PC specs in the morning, but in the meantime, does anyone know how to fix this?

It's *going to be* a Xubuntu only system, and I've tried to repair the GRUB files via the Live CD and [here](http://ubuntuforums.org/showthread.php?t=1195275).

Any ideas?

---

### Post by Quackers on 2011-01-15
Welcome to UF
Please boot from the Ubuntu (or Xubuntu) Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Westie. on 2011-01-16
Righty, here you go:

[http://westie.pastebin.com/NSnF2T2T](http://westie.pastebin.com/NSnF2T2T)

Okay, how does go about wiping the MBR of the 2nd drive?

---

### Post by dino99 on 2011-01-16
sudo dpkg-reconfigure grub-pc

---

### Post by presence1960 on 2011-01-16
make sure sda is set to boot first in the hard disk boot order in BIOS. sdb does not have a partition table and booting from that will result in a boot failure.

---

