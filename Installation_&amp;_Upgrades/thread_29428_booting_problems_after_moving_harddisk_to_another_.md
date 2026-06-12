---
title: "booting problems after moving harddisk to another computer"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by dgo on 2005-04-24
hi there,

i installed ubuntu warty 4.10 on a computer using default partitioning and so on.
the installation was successfull and i worked a lot with it.

now, i wanted to put the harddisk into a new computer.
ubuntu now stops at bootup with the lines:

"grub loading stage1.5"


"grub is loading please wait..."

and that's it....when i put the harddisk back to my old computer, everything works completely fine again.

i am close to getting mad

can you help me?

thanks and greetz

florian

---

### Post by cowbud on 2005-04-24
This is mostly likely because when you moved the drive from one system to another its location in the system changed (i.e. /dev/hda or /dev/hdb or in grubs case hd(0,0) or hd(0,1) ) What you need to do is boot up with a boot disk (There are rescue disks all over the place and you can use the ubuntu live cd/install cd depending on how you want to appraoch the problem) and find out where the drive is located once you have you need to reconfigure and reinstall grub. 

/boot/grub/menu.lst will need to be looked at and you will need to know how to manually mount your drives 

There are a lot of variables that come in to play here and other complications that could come up but overall if you know how to mount drives and use the command line you should be able to figure it out. I suggest also asking on the irc channel to get more of a "live" help.

---

### Post by dgo on 2005-04-24
well, the thing is that the drive is the only one in the system. so hd0 should remain hd0 even on  the new computer, please correct me if i am wrong. when i boot with a live-cd i can mount the harddisk with mount /dev/hda1 /mnt/hda1 and see the entire filesystem.
and when i do:
```
sudo mount /dev/hda1 /mnt/hda1
chroot /mnt/hda1 /bin/bash
grub
root (hd0,0)
setup (hd0)
quit

```

everything works completely fine. i hoped to be able to fix the problems with that but no.
the funny thing is that when i boot with a bootdisk grub shows the menu but when i select a boot option it stops after the following lines:
```
root (hd0,0)
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
```

---

### Post by dgo on 2005-04-25
okay, seems like there's no comfortable solution to that problem.

i will have to reinstall ubuntu from scratch and restore all important data afterwards.

seems like the kernel does not match with new controllers and so on.

to mods: please close this thread

---

### Post by paxmark on 2005-05-03
[QUOTE=dgo]okay, seems like there's no comfortable solution to that problem.

i will have to reinstall ubuntu from scratch and restore all important data afterwards.

seems like the kernel does not match with new controllers and so on.

to mods: please close this thread[/QUOTE]
 Yeah, new install.  It probably has a different video card, and other various drivers. Oftentimes you won't even be able to swap bootable hard drives from computer to computer in windows either.  However, it is easier to keep your /home when you have to reinstall your system in linux

---

