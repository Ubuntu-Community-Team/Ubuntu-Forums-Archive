---
title: "GRUB2 Install apparently fails on Alt. CD"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by JustinR on 2011-02-06
Hey everybody,

I'm following this guide to reinstall Ubuntu on my computer because of a seemingly untraceable software bug concerning my CPU, but **testing it in a VM first**:
[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)

The basic gist of it is to create an encrypted dm-crypt/LUKS partition and then a LVM setup.

I'm using an Ubuntu 10.10 Alternate CD disk in Advanced Mode.

I have no problems with the guide, but at the installation step of installing GRUB2, it fails, without giving me a remotely helpful error message. It tells me installation on '/dev/sda' (MBR install) failed at 50% and thats pretty much it.

So I'm I missing something? Should I be installing GRUB2 somewhere else? Like on the LVM volume/logical group?

Here's my HDD setup:
(20 GB VirtualBox HDD)
-1 Encrypted partition with dm-crypt
--1 LVM Volume Group
---3 LVM Logical Groups (/,home,swap)

__

By the way, **there is no separate /boot partition**, to my understanding GRUB2 can handle encrypted LVM's without a separate /boot partition without issue? Is this my problem?

After trial/error and combined searching for a solution for 8 hours I'm at a loss. I've looked at these pages and much much more:
[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1205372](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1205372)
[http://ubuntuforums.org/showthread.php?t=1305409](http://ubuntuforums.org/showthread.php?t=1305409)
[http://forums.aria.co.uk/showthread.php?t=16377](http://forums.aria.co.uk/showthread.php?t=16377)

I've also used live-cd's to chroot into the encrypted LVM environment and install grub and trying other things but nothing works. And most documentation is outdated. I haven't tried any other boot loaders like SysLinux or LILO, I would like to get GRUB2 to work.

Thanks, any suggestions are welcome.

---

### Post by echo6 on 2011-02-06
The /boot partition can not be encrypted!

---

### Post by JustinR on 2011-02-06
> **echo6 said:**
> The /boot partition can not be encrypted!

Yeah I finally found that out at around 2AM. :D

Thanks for the reply though!

---

