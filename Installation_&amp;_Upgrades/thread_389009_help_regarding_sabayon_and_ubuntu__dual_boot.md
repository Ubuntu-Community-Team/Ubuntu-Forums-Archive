---
title: "help regarding sabayon and ubuntu  dual boot"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2007-03-20
ubuntu is installed on hda1 , i installed sabayon 3.3 on hda2 WITHOUT installing grub . now i need to figure out how to add a proper sabayon entry into ubuntus grub. can anyone help me out.. ive searched for the menu.lst entry for sabayon 3.3 on the live dvd.. and it was not there. i have no idea what the entry should look like on my grub menu.lst

my current grub menu.lst looks like this

```
## ## End Default Options ##

splashimage=(hd0,0)/boot/grub/53133-debian21.xpm.gz

title		Ubuntu, kernel 2.6.20.1
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20.1 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.20.1
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.20.1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20.1 root=/dev/hda1 ro single
boot

title		Ubuntu, kernel 2.6.20
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.20
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.20 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.20
boot
```

---

### Post by hogwartsnigel on 2007-11-28
Raffy Taffy,
I am afraid I'm not posting to help but to say I'm watching with interest as I've just installed Sabayon on a seperate partion to Ubuntu and didn't install the grub either. I too am looking to have a guide to point in the right direction of changing the ubuntu grub to point to Sabayon as a loading option too.. ta
Nigel

---

