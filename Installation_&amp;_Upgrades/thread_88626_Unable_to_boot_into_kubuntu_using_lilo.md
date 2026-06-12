---
title: "Unable to boot into kubuntu using lilo"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by arubin on 2005-11-10
I have a lilo boot at the moment which I prefer to grub. I can run lilo from my slackware installation. My problem is that kubuntu will not run. The boot starts but then halts with errors of /etc/fstab not being present.

My lilo.conf has
image=/mnt/hdb6/boot/vmlinuz-2.6.12-9-386
       label ="kubuntu"
       root=/dev/hdb6
      initrd=/mnt/hdb6/boot/initrd.img-2.6.12-9-386
      read-only

which corresponds with what was in image.lst for grub

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

This worked when with grub, but what looks like a corresponding section in lil.conf does not work. It seems that the root is not being located correctly. I reaaly prefer lilo to grub. What do I need to do to get kubuntu working with lilo?

Thanks

---

