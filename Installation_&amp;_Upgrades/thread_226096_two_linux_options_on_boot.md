---
title: "two linux options on boot?"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by stalefist on 2006-07-30
hello all, im completely new to linux, lets just get that set in stone now :P so i booted up my laptop and where it would normally have the option to select my os theres linux 386, linux 386 recovery mode, and what not. well i just saw now that theres an extra set of linux 386 and recovery mode options, as in it says it twice. is this normal or did i break something already :/

---

### Post by XAsmodeanX on 2006-07-30
You probably got a kernel update so if they both say Ubuntu, one is the old kernel and the other is the newer.

---

### Post by Boomy on 2006-07-30
If you don't want to see all of those, you can edit your /boot/grub/menu.lst by putting a "#" in front of the entries you don't want to show up. 

i.e

#title		Ubuntu, kernel 2.6.15-26-686
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-686
#savedefault
#boot

---

