---
title: "Grub error 22 on clean install"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by Hans5849 on 2006-09-09
Grub is currently giving me the error 22 after stage 1.5, i checked and everything is set right.

device.map
```

(hd0)    /dev/hdc
(hd1)    /dev/hdd
(hd2)    /dev/sda
(hd3)    /dev/sdb
(hd4)    /dev/sdc
(hd5)    /dev/sdd

```
menu.lst
```

default        3
timeout        10

title        Ubuntu, kernel 2.6.15-26-386
root        (hd5,1)
kernel        /vmlinuz-2.6.15-26-386 root=/dev/sdd5 ro quiet splash
initrd        /initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd5,1)
kernel        /vmlinuz-2.6.15-26-386 root=/dev/sdd5 ro single
initrd        /initrd.img-2.6.15-26-386
boot

title        Ubuntu, memtest86+
root        (hd5,1)
kernel        /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows XP Professional
rootnoverify        (hd5,0)
makeactive
chainloader    +1

```
So the locations appear to be correct, so i have no idea what to do.

I may have spotted the problem but because im running from a live CD im still going to post this.

---

### Post by HeLiS on 2006-09-13
Im having this exact same problem on my computer. Would love to know how to fix it or even better how to change it to LILO instead of GRUB

---

### Post by confused57 on 2006-09-13
> **HeLiS said:**
> Im having this exact same problem on my computer. Would love to know how to fix it or even better how to change it to LILO instead of GRUB

Here's how to install Lilo:

[http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal](http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal)

---

