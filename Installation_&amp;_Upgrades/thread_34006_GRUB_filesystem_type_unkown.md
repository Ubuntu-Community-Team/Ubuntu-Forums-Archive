---
title: "GRUB: filesystem type unkown"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by transkinetic on 2005-05-13
Here's my process and troubling result with grub. If I haven't provided enough infornation or clarification, please say so.

Two drives in computer.
60gb and 10gb
Installed ubuntu on 60gb drive (hd0,0)
Swapped (hd0,0) and (hd1,0)
10gb drive is now first.
Installed windows xp to 10gb drive. (hd0,0)
Swapped drives back.
Ubuntu --> (hd0,0)
XP --> (hd1,0)

Grub, of course did not detect XP as it was installed before XP was.

sudo gedit /boot/grub/menu.lst

title wintendo
root (hd1,0)
savedefault
makeactive
chainloader + 1

Attempting to boot entry 'wintendo' causes an error:
Filesystem type unknown, partition type 0x7

Appreciate any help.

---

### Post by spd106 on 2005-05-13
Hi, i think the problem here is that windows can't boot from a non-first disk, so to solve this you need to "virtually swap" the disk drives.

This is usually achieved by putting the following lines it your menu.lst on the next line after the title.
map (hd0) (hd1)
map (hd1) (hd0)


For further information look at the grub website
[http://www.gnu.org/software/grub](http://www.gnu.org/software/grub)

You could also try reinstalling grub.

Hope this helps

---

### Post by transkinetic on 2005-05-13
Thanks spd, worked perfectly.

---

