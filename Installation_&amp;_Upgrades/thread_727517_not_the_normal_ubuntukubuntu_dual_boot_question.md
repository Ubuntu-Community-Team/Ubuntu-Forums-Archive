---
title: "not the normal ubuntu/kubuntu dual boot question"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by bangkok on 2008-03-17
ok so here is my intention... run ubuntu feisty as my main distro (having irritaing issues with ubuntu gutsy on another computer) & kubuntu gutsy as an alt distro to basically run manslide (killer kde slideshow app).

kubuntu was installed after ubuntu so it's grub has been installed in the mbr (hd0) i am assuming. kubuntu boots a-ok. ubuntu (included in kubuntu's menu.list & looks fine) boots ok until GDM & then i get dumped to a shell root prompt (strange that a root prompt is available without any authentication but that's a question for another time). if i issue
> shutdown -r now 
the computer doesn't actually shutdown but actually starts GDM & gets me to my ubuntu login screen & then everything is as it should be.

so this is what my menu.lst file in kubuntu looks like:
> title		UBUNBTU - FESITY - Ubuntu, kernel 2.6.20-16-generic (sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
 savedefault
boot


title		KUBUNTU - GUTSY - Ubuntu 7.10, kernel 2.6.22-14-generic (sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d668e6c5-786d-404c-83a2-0f27eb0d11a8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


title		UBUNBTU - FESITY - Ubuntu, kernel 2.6.20-16-generic (recovery mode) (sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


title		KUBUNTU - GUTSY - Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d668e6c5-786d-404c-83a2-0f27eb0d11a8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic


title		UBUNBTU - FESITY - Ubuntu, memtest86+ (sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


title		KUBUNTU - GUTSY - Ubuntu 7.10, memtest86+ (sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


hope someone might have a good idea of what might be the problem.

thanks in advance

---

### Post by zvacet on 2008-03-18
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

title UBUNTU - FESITY - Ubuntu, kernel 2.6.20-16-generic (sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic

title UBUNTU - FESITY - Ubuntu, kernel 2.6.20-16-generic (recovery mode) (sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title UBUNBTU - FESITY - Ubuntu, memtest86+ (sda5)
root (hd0,4)
kernel /boot/memtest86+.bin
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title KUBUNTU - GUTSY - Ubuntu 7.10, kernel 2.6.22-14-generic (sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d668e6c5-786d-404c-83a2-0f27eb0d11a8 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

title KUBUNTU - GUTSY - Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d668e6c5-786d-404c-83a2-0f27eb0d11a8 ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

title KUBUNTU - GUTSY - Ubuntu 7.10, memtest86+ (sda6)
root (hd0,5)
kernel /boot/memtest86+.bin
savedefault
boot

```
sudo update grub
```

---

### Post by bangkok on 2008-03-19
zvacet thanks for the reply.

after saving back-up of my menu.lst in /boot/grub (sda5 - ubuntu feisty partition) &  the making modifications showns to menu.lst shown i ran:

```
sudo update-grub
```

never knew of that command before. but it ran ok from the command line but changed the menu.lst file just modified above to look like:

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f365b1cb-fa76-48b0-9f53-c2528d5d7eb4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title KUBUNTU - GUTSY - Ubuntu 7.10, kernel 2.6.22-14-generic (sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d668e6c5-786d-404c-83a2-0f27eb0d11a8 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

title KUBUNTU - GUTSY - Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d668e6c5-786d-404c-83a2-0f27eb0d11a8 ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

title KUBUNTU - GUTSY - Ubuntu 7.10, memtest86+ (sda6)
root (hd0,5)
kernel /boot/memtest86+.bin
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

with the same problem happening after re-booting, being dumped to a root prompt which will resume booting after either:

```
shutdown -r now
```

or CTRL-D keystroke.

might i have missed something in there?

appreciate the feedback, thanks

---

