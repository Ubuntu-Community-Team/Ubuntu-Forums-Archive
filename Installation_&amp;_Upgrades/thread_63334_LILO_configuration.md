---
title: "LILO configuration?"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by Canuckistan on 2005-09-07
Hello, I'm a Linux newbie who just installed Ubuntu the other day. GRUB wouldn't install so I was forced to install LILO. I have 3 partitions, 1 with WinXP Pro on it, and 1 with Ubuntu on it. I've got Ubuntu booting ok, but I would like to setup a dual-boot system.  I was wondering if anybody could tell me how to edit my lilo.conf file to do that? Here is what the file currently looks like.

boot=/dev/hda2
root=/dev/hda2
compact
install=/boot/boot.b
map=/boot/map
vga=normal
delay=20
image=/vmlinuz
label = Linux
read-only
initrd=/initrd.img

Many thanks in advance.

---

### Post by wvslkr on 2005-09-07
[http://www.acm.uiuc.edu/workshops/linux_install/lilo.html](http://www.acm.uiuc.edu/workshops/linux_install/lilo.html)

That should get you going.

---

### Post by Canuckistan on 2005-09-07
Thanks for the link.

---

