---
title: "some problems with booting...."
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by rw30 on 2005-05-03
firstly, sorry for my poor english :  )  I know I make a lot of mistakes, hope my post will by understandable  :  )

my [one and only :  ) ] hdd looks like that:
partition  1: NTFS [primary, active, win32 installed]
p2: FAT16 [primary, no OS]
then the extended partition:
logical disc 1: linSWAP
logical disc 2: reiserFS [ubuntu]
logical disc 3: reiserFS [slack10]
locical disc  4: NTFS

on the beginning it was only windows installed there, then I added ubuntu and everything was correct [using GRUB], but finally I decided to install slackware, and that when my problems started : 
during slack's setup it installed LILO into my mbr, that doesn't recognized my OSs  correctly, so I decided to clear my mbr so now the only system I have access to is windows
I don't know how to enable some nice bootloader [I mean GRUB] back to have access to all systems

friend of mine told me to use some liveCD distribution and then use
 * grub-install /dev/hda * 
command, but it doesn't work [I was trying to use mepis or knoppix to do that]:  
mepis gives error: 
[i]
Probing devices to guess BIOS drives.This may take a long time [.........]
sed: can't read /boot/grub/device.map: No such a file or directory
grep: /boot/grub/device.map: No such a file or directory
/dev/hda  does not have any corresponding BIOS drive [/i]

knoppix can't even find [probably just doesn't posses :  )] /boot/grub directory

because it looks like the only problem [under mepis] is missing device.map file I was trying to copy that file from ubuntu's /boot/grub dir, unfortunately I got no rights to write in mepis' /boot/grub dir  [even despite being root and theoretically having all possible acces in that dir]

so, as a linux *megalame* I can't help myself and hope you guys help me

regards,
rw30

---

### Post by rw30 on 2005-05-03
I DID IT !  : )

I've installed GRUB using ubuntu installCD in rescue mode : )

Now just need to add some new lines to GRUB's menu.lst to be able to boot slack and that's all :  )

---

