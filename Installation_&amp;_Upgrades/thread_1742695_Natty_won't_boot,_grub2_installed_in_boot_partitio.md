---
title: "Natty won't boot, grub2 installed in boot partition because Truecrypt MBR"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by linuxone on 2011-04-29
Hi,

after upgrading 10.10 to Natty 11.04 my Kubuntu 64-bit System won't boot anymore.

During upgrade an error message appears, saying GRUB2 cannot be installed into a partition (something about bad idea and blocklist).

First reboot shows this error message:
```
Error: symbol not found: 'grub_env_export'
```

I tried to repair GRUB2 by using a Live CD, mounting all needed partitions, chroot to my installed system and running update-grub2. This time no error message appears.

Next reboot the system does hang, showing "Booting..." for minutes. Nothing happens.

I'm using a partition boot loader (for Linux) since years on my Netbook / Notebook. Due to security reasons all partitions of the mobile device were encrypted. Unfortunately I also need an Windows system, so the first partition contains an Win 7 installation encrypted with Truecrypt.
Truecrypt needs to be installed into the MBR (as far as I do know and from my first tests some times ago). So I installed the Linux bootloader into the /boot partition (sda6).
Linux root partition is also encrypted using cryptsetup/Luks.

How can I fix this problem, keep my Truecrypt/Windows system and boot the encrypted Linux system?

Thomas

---

### Post by dino99 on 2011-04-29
found this if it can help:

[http://indoors.jmones.net/2010/09/21/notes-on-chainloading-truecrypt-from-grub2-install-grub2-on-primary-partition/](http://indoors.jmones.net/2010/09/21/notes-on-chainloading-truecrypt-from-grub2-install-grub2-on-primary-partition/)

[https://gitorious.org/grub2tc#more](https://gitorious.org/grub2tc#more)

---

### Post by linuxone on 2011-04-29
Hi,

thanks for the interesting links. Unfortunately these hints cannot really solve my problem.

After a number of tests (supergrub, supergrub2, rescatux, repair from Live-DVD and more...) I found a solution myself:

Remove (purge!) all grub2 packets, then install grub (version 1), run "grub-setup /dev/sda6" and everything is working as it should be.

I did use grub2 since it became the default Ubuntu bootloader without any problems. I don't understand why it does produce this partition install problem now.

Thanks.
Thomas

---

### Post by dino99 on 2011-04-29
good feedback, thanks

---

