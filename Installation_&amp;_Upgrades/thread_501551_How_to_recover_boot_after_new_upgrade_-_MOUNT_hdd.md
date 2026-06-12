---
title: "How to recover boot after new upgrade - MOUNT hdd"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by decatett on 2007-07-15
hdd = /dev/hda3
file systems = ext3
mount location = /media/1

1. boot from ubuntu live cd
2. "sudo mkdir /media/1"  make mount location
3. "sudo mount -t ext3 /dev/hda3 /media/1" mount old hdd 
4. "sudo gedit /media/1/boot/grub/menu.lst" edit boot loader - grub
5. in new file change 



title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=[COLOR="DarkRed"]**[SIZE="3"]hda1[/SIZE]**[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
with:
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''



title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=[COLOR="DarkRed"]**[SIZE="3"]hda3[/SIZE]**[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault


6. save and restart

---

