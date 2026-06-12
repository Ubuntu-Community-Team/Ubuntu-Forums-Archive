---
title: "Can't install xubuntu"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by Jimjim438 on 2013-02-26
So when I try to install it it makes me choose my language and makes me choose whether I want to download updates and third party software as I'm installing, but then it takes me to this screen where I have to choose these devices: /dev/sda, /dev/sda1, /dev/sda2, /dev/sda3, and all of them have "ntfs" under "Type". It also makes me choose a device for boot loader installation but no matter what I do when I try to install it. the window just disappears and nothing happens!

---

### Post by Bashing-om on 2013-02-26
Jimjim438; OH ! Dear, not much to work from.

Dual booting ? (did you set up the ubuntu partition ???)
What version are you attempting to install ?
How new or old is the machine you are attempting to install onto ?
ntfs partitions -> is this a WUBI install ?


See if these help ya.
[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)
[http://ubuntuforums.org/showthread.php?t=2080356](http://ubuntuforums.org/showthread.php?t=2080356)
[https://help.ubuntu.com/community/Troubleshooting](https://help.ubuntu.com/community/Troubleshooting)

Further advise pending.
[INDENT][INDENT]hope this helps

[/INDENT][/INDENT]

---

### Post by UltimateCat on 2013-02-26
Hi:

It might be helpful to look at all of the partitions on your computer.
To do so with a Live CD open the terminal and run this command as root:
```
fdisk -l

```

That's the small letter 'l' not the capital L

>  /dev/sda, /dev/sda1, /dev/sda2, /dev/sda3, and all of them have "ntfs"

NTFS is a indication that you have a Microsoft Windows partition on your system.

Before I could put Linux on my laptop I had to shrink my Windows 7 partition.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Hope this helps

---

### Post by Jimjim438 on 2013-02-26
> **Bashing-om said:**
> Jimjim438; OH ! Dear, not much to work from.

Dual booting ? (did you set up the ubuntu partition ???)
What version are you attempting to install ?
How new or old is the machine you are attempting to install onto ?
ntfs partitions -> is this a WUBI install ?


See if these help ya.
[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)
[http://ubuntuforums.org/showthread.php?t=2080356](http://ubuntuforums.org/showthread.php?t=2080356)
[https://help.ubuntu.com/community/Troubleshooting](https://help.ubuntu.com/community/Troubleshooting)

Further advise pending.
[INDENT][INDENT]hope this helps

[/INDENT][/INDENT]
Yes I am attempting to dual boot
12.10
Fairly new bought it last year
No I'm using this program called "UNetbootin" so I can install without a disk

---

### Post by Bashing-om on 2013-02-26
Jimjim438;

These tutorials I expect will get ya within the "ball park"// Unknown at this time if UEFI or "smart response" is a factor in the installation process.

[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

Please post back with any request for additional assistance.

[INDENT][INDENT]best regards

[/INDENT][/INDENT]

---

