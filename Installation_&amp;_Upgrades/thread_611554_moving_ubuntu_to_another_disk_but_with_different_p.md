---
title: "moving ubuntu to another disk but with different partitions"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by lptr on 2007-11-13
My idea was to simply move over a complete machine from one HDD to a bigger one, as I did successfully in the past, several times.

The only difference to the past is, that the old installation on HDD1 has had a seperate boot partition. HDD2 should not having this one, but should be placed into root partition (still seperate on sda1) /boot.

I fiddled around and changed /etc/fstab to the new UUIDs to correctly mounting drives (I made it simple and installed a base system with layout / /home swap on HDD2 and noted the newly generated UUIDs).
In /boot/Grub/menu.lst similar things were changed.

Probably I missed something to change anywhere because, only Grub appears after reboot like this:

grub>

Any ideas?

rob*

---

### Post by lptr on 2007-11-13
Seems that it is not so easy - hm...?

Maybe not being read because I should have name it like this:

With different partition layout moving an Ubuntu installation.

rob*

---

