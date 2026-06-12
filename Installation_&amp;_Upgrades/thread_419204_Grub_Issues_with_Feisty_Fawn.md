---
title: "Grub Issues with Feisty Fawn"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by paradoxsystems on 2007-04-22
Well I have 2 SATA drives (sda and sdb) and 1 Removable IDE hard drive (hdc)

I already have ubuntu and XP on sda with grub working fine...

I installed Feisty Fawn on hdc1

I try and boot from grub to Fawn and it comes up error 25: disk read error.
I know the harddrive is good and all the files are there...


It comes up with the old grub on sda so I had to edit device.map

```
(hd0)	/dev/sda
(hd1)	/dev/hdc
```

so my menu.lst looks like:


```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

[COLOR="Lime"]title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
boot[/COLOR]

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot
```

The green is my removable hard drive hdc that I want to boot to but won't let me.

any advice???

---

### Post by pepsi_max2k on 2007-04-22
any reason why /dev/hdb isn't hd1? have you tried other hdXs in menu.lst instead?

---

### Post by paradoxsystems on 2007-04-22
Yes, I have tried,

hd1,0
hd1,1

and nothing happens

---

### Post by pepsi_max2k on 2007-04-22
hd2,0?

---

