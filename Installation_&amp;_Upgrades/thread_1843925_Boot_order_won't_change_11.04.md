---
title: "Boot order won't change 11.04"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by dulciepercy on 2011-09-14
Hi

Dual boot machine with 11.04 and Windows 7 64 bit.  I need it to boot into Windows by default but nothing I do will make the boot order change and it always goes ubunting.

update-grub gives:

Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

startup manager sets GRUB_DEFAULT=8 in etc/default/grub which is to be expected.  But it still boots into Ubuntu, no matter what number I put there.

Any ideas?

Thanks

---

### Post by dulciepercy on 2011-09-14
Good grief.  I've been trying to sort this out for weeks, and as soon as I pose in the forum it works itself out!

The correct number was 5.  Doesn't explain why it didn't work properly before.  Presumable my fault.;)

---

