---
title: "Unable to access Linux after dual boot install"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by dbryant32 on 2008-11-03
Vista is on /dev/sda1
Ubuntu is on /dev/sda2
Swap on /dev/sda3

Installed boot loader to /dev/sda2

Booted to vista and ran Easy BCD

Added entry for Ubuntu:
Told it Grub was not installed to the boot sector
pointed it to Partition 1 (Linux Native 32GB)

She won't boot
I get to a grub> menu and that's it.:icon_frown:
HELP!!

---

### Post by openBA on 2008-11-03
Hi dbryant32,

I did same a few months ago, installed Ubuntu after Vista without any problems. Ubuntu setup installed grub and taked care about everything.

Please check /boot/grub/menu.lst

I suppose there should be something wrong.

br

---

### Post by mactece on 2008-11-03
I'm no expert but whenever I've had dual boot problems I've been able to overcome them with Supergrub.
This is a link to a thread I started to deal with a different issue but it has some links and thoughts I think you might find useful if you can be bothered to read through it all.

[http://ubuntuforums.org/showthread.php?t=569847](http://ubuntuforums.org/showthread.php?t=569847)

Good luck
David

---

### Post by dbryant32 on 2008-11-04
I decided to let grub install to the boot sector and handle everything. It's working fine now.:guitar:

---

