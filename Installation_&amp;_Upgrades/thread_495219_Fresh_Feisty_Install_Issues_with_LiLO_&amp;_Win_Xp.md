---
title: "Fresh Feisty Install Issues with LiLO &amp; Win Xp"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by masinger53 on 2007-07-07
Hello, all:  Not sure if this is right place to ask this, but here goes.

Just did fresh reinstall of Feisty on my Sager NP5760 laptop with existing Windows XP Pro partition from alternate install 64bit CD.  This was due to issues with GRUB and this hardware BIOS causing the optical drive to disappear from both OSs.  After some research, found some tips regarding the use of LiLo instead.  So, I did a reinstall rather than muck about with replacing the GRUB.

Install went fine; optical drive is now visible to Linux; however, LiLo doesn't bring up a menu and won't boot XP even if I change the default in lilo.conf.

Its been a really long time since I've used LiLo and I can't see what I've done wrong in the configuration.

A second set of eyes or a smack upside the head would be greatly appreciated.

Oh, and here is my lilo.conf, minus comments and extra white space:

boot=/dev/sda
map=/boot/map
delay=200

default=Linux
image=/vmlinuz
        label=Linux
        read-only
        append="root=/dev/sda2  "
        initrd=/initrd.img
image=/vmlinuz.old
        label=LinuxOLD
        read-only
        optional
        append="root=/dev/sda2  "
        initrd=/initrd.img.old
other=/dev/sda1
        label=Windows

---

### Post by masinger53 on 2007-07-11
My bad -- misspelled windows when I tried the default; menu comes up if I press the Shift key.  =)

Both the OSs are present in the menu and boot properly and the optical drive is now visible to both as well.

---

