---
title: "[SOLVED] Intrepid Install - dmraid - Grub ERROR 15"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by scurry7 on 2008-11-04
I have installed Hardy with some help from the forums, now I am trying to get Intrepid going.  An distro-upgrade didnt go so well now I am trying it from a new install:

I have to use dmraid to get gparted to read the partitions correctly.  After install I have trouble with grub...



This is what I did:
1. boot live disc
2. when I get to the part of the install about partitions I....
ctrl+alt+f2 > apt-get update > apt-get install dmraid > ctrl+alt+f7

here is my partition setup:
```
/dev/mapper/nvidia_debdjei
   /dev/mapper/nvidia_debdjei1   type=ntfs
   /dev/mapper/nvidia_debdjei2   type=ext3   mountpoint=/   (format during install)
   /dev/mapper/nvidia_debdjei3   type=ext3   mountpoint=/home   (no format)
   /dev/mapper/nvidia_debdjei4   type=swap
```

I finish the install

Note: at step 7 of 7 of the setup I click advanced > install boot loader checked is checked > device for boot loader = (hd0) ...(these are the default option)...


system installs....I reboot.....


error:
```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
```


my question:  does dmraid get installed with the default install of ubuntu (since I installed it while in the live setup cd)?

(so maybe Error 15 (file not found) cant be found because dmraid is not here to setup the /dev/mapper/nvidia_debdjei.  ???

help please!

---

### Post by scurry7 on 2008-11-04
...bump...

any ideas anyone?
por favor?

---

### Post by scurry7 on 2008-11-04
figured it out...I will post more info on how I did in-case someone else has my same prob.

[This site ]("http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/")helped a ton! ([http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/))

---

### Post by scurry7 on 2008-11-05
fixed..[here]("http://ubuntuforums.org/showthread.php?t=972068") is my walkthrough/howto: [http://ubuntuforums.org/showthread.php?t=972068](http://ubuntuforums.org/showthread.php?t=972068)

---

