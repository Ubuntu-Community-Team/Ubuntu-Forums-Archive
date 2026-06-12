---
title: "help with grub and slack 10.2"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by Requiem on 2005-10-26
I can't for the life of me, (re)instal grub on the mbr of hda

I've run grub-install hd0,0
it even says that there are no errors, why does it keep on printing
boot disk error when I try to boot from hda?

and if anybody has any experience with slack 10.2, what are the grub settings necesary to boot it?

---

### Post by Xian on 2005-10-26
[QUOTE=Requiem]I've run grub-install hd0,0
it even says that there are no errors, why does it keep on printing
boot disk error when I try to boot from hda?[/quote]
Try another method:
$ sudo grub-install /dev/hda

If still problems then post the exact error message.

[QUOTE=Requiem]and if anybody has any experience with slack 10.2, what are the grub settings necesary to boot it?[/QUOTE]

title		Slackware 10.2
root		(hd0,2)
kernel		/boot/vmlinuz-generic-2.6.13 root=/dev/hda3 ro
initrd		/boot//boot/initrd.gz

If you are using the default kernel you don't need the initrd line.
Change the partition numbers for your own system.

---

