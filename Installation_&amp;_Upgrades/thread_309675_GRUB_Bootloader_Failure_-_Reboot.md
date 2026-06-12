---
title: "GRUB Bootloader Failure - Reboot"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by Gamzarme on 2006-11-29
Hey all. I'm very new to the Linux scene and I decided to choose Ubuntu as my starting/learning distro.

Right now I'm trying to boot up Ubuntu 6.10 "Edgy Eft" Server Edition. The computer I have it installed to is a Pentium 233MHz with 96MB of RAM.

The installation procedure went with some difficultly but after a few tries it all went as detailed in an [installation guide]("http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html") I found. However, after installing it needed to reboot and did so.
Following this, GRUB began to start up, it loaded 1.5 and then proceeded to start up. Then it gave a three second countdown with the option to ESC before it rebooted itself and ran into the problem again.

I'm wondering why GRUB doesn't seem to work properly. It's very frustrating as I have no clue what I'm doing or where to go. Will someone please help with this issue?

Additionally, I tried booting with the install CD and when it came up with a list of option to perform (install to hard drive, check for errors, etc) I then chose boot from hard drive (the last option in the list) and it started to load GRUB again. The error message this time was:
```
booting from local disk...
isolinux: Disk error 05, AX = 0000, drive 80

Boot failed: press a key to retry...
```

I then pressed a key and it started to reboot process over again. So, there it is, I've tried booting with the CD and with the IDE01 hard drive, nothing works at the moment. But perhaps there is a command I can use to bypass GRUB..or reinstall only the potentially corrupted GRUB install.

Thanks for your assistance. =)
-Patrick

---

### Post by Gamzarme on 2006-12-05
Will anyone please help me? I'm really wondering about this setup as I'd like to get the server up and running.

---

