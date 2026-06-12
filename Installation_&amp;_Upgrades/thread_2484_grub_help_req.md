---
title: "grub help req"
date: 2004-10-28
forum: Installation &amp; Upgrades
---

### Post by Tyro on 2004-10-28
I've installed Ubuntu onto my 2nd HDD - hdb1 but did not use grub to write to mbr as I have Mepis as my main OS on this machine.

Could someone tell me what entries to make in mepis grub to allow multi booting between Ubuntu and Mepis. 

Existing menu.lst =
default saved
timeout 15
color cyan/blue white/blue
foreground ffffff
background 2f5178
splashimage /boot/grub/mepis.xpm.gz

title MEPIS at hda1, kernel 2.6.7
kernel (hd0,0)/boot/vmlinuz-2.6.7 root=/dev/hda1 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,0)/boot/initrd.mepis 
savedefault

title MEPIS at hda1, kernel 2.4.26 ......

Thanks 

Tyro :)

---

### Post by jdong on 2004-10-28
```

title           Ubuntu, kernel 2.6.8.1-3-X86
root            (hdX,Y)
kernel          /boot/vmlinuz-2.6.8.1-3-X86 root=/dev/hdXN ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-3-X86
savedefault
boot

```

Replace all capital letters with your appropriate values. (and you know I wasn't talking about the first U) 8)

---

### Post by Tyro on 2004-10-29
[QUOTE=jdong][code]
root            (hdX,Y)
kernel          /boot/vmlinuz-2.6.8.1-3-X86 root=/dev/hdXN ro quiet splash
[/QUOTE]


Set menu.lst as
root            (hdb,0)
kernel          /boot/vmlinuz-2.6.8.1-3-X86 root=/dev/hdb1 ro quiet splash

I keep getting - "Error 23: error while parsing number.    Press any key" 
and goes back to grub. 

Can you help?

Tyro :)

---

### Post by cacofonix on 2004-10-29
[QUOTE=Tyro]Set menu.lst as
root            (hdb,0)
kernel          /boot/vmlinuz-2.6.8.1-3-X86 root=/dev/hdb1 ro quiet splash

I keep getting - "Error 23: error while parsing number.    Press any key" 
and goes back to grub. 

Can you help?

Tyro :)[/QUOTE]
It looks like you have a typo you need to add another 0 to root ie root (hdb0,0) everything else looks correct

good luck

---

### Post by Tyro on 2004-10-31
I put the additional "0" in hdb0,0
But still get the same error messeage!

Tyro :)

---

### Post by bvc on 2004-10-31
your second hd is going to be diff than hda, usually hdb. What does
fdisk -l
say?

You want something more like
```
title Ubuntu, kernel 2.6.8.1-3-386
kernel (hd1,0)/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdb1 nomce psmouse.proto=imps
initrd (hd1,0)/boot/initrd.img-2.6.8.1-3-386
savedefault

```

the 1 in hd1,0 is for hdb
the 0 in hd1,0 is for the first partition


so

hd1,0
and
hdb1

is the same thing.

---

### Post by Tyro on 2004-10-31
BVC: Thats got it up and running, thanks for that.


Scared the life out of me when it did an auto update and upgrade on first boot  ;)

Tyro :)

---

