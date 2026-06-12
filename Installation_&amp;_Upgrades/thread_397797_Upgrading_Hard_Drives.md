---
title: "Upgrading Hard Drives"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by isaiah55 on 2007-03-31
I know that this must have been covered somewhere else but I can't find a post that is similar to my situation.
Basically I have 2 ide Hard Drives
One hard drive has the OS on it (Ubuntu - no Windows here :))
The other has my home directory on it.

I recently got hold of 2 second hand SATA drives.
I would like to copy what I have on each ide drive on to its respective Sata drive.
I need to do this because I am a bit of a linux newb and don't want to go through the heart ache of setting up my linux box just the way I like it, with webmin, samba, dansgaurdian etc etc.
I would also like to format the ide drives when finished and leave on of them on the system for more data storage.

I hope someone can give me a step by step guide or at least point me in the right direction, outlining the things I need to look out for.

Thanks in advance

Cheers

Isaiah 55:8,9

---

### Post by andi on 2007-03-31
hi isaiah55,

i hope you can make the transition to your new drives with my little howto. but please note this howto is not newbie safe :) . this means you need basic knowledge about linux filesystems, partitions, the meaning of /etc/fstab, grub and the linux console tools like cp and chroot. please read the howto to the end before doing anything! then make sure you understand what is done in the various steps of the howto! any incorrect interpretation of the commands and you can say goodbye to your data!

first of all install the new harddrives. then make sure your bios is able to boot from sata. most often you need to set your first boot device to scsi or sata (only check this don't do it now!!!). if your sata controller does support raid you must append your drives to raid containers. for this step you must consult your mainboard/controller manual. if you don't append your harddrives to a raid container your bios won't find the boot drive. (it took me at least one hour to sort this out the last time :) ).

after that boot the computer up. install gparted if you have GNOME or qtparted if you have KDE. look in to your /etc/fstab for the layout of your harddrives and create the same layout on your new harddrives (dev/sda and /dev/sdb) with the tool. the size of the new partitions must be the same or bigger. make double sure that you edit the correct drives before you finalize this step!!

create temporary directories with where you can mount the new partitions to. you should try to simulate your drive layout with the temp. directories for example ```
mkdir sda1 sda1/boot sda1/home sda1/usr
```
mount your partitions to the directories with ```
sudo mount /dev/sda1 sda1
sudo mount /dev/sda2 sda1/boot
sudo mount /dev/sda5 sda1/home
sudo mount /dev/sda6 sda1/usr
```
copy now your data to the new drives. you can do this with ```
sudo cp -pxr SOURCE DESTINATION
``` make sure you copy the data according to your harddrive layout to the correct partitions. the "x" flag makes sure you stay on the current filesystem and do not copy across filesystems.

do a chroot to your new root partition ```
sudo chroot sda1 /bin/bash
```(if sda1 is your root partition).

edit the grub menu.lst ```
sudo gedit /boot/grub/menu.lst
``` accordingly to your new requirements. change ```
# groot=(hdX,X)
``` and every ```
root            (hdX,X)
```.
next do a ```
grub
``` and ```
root (hdX,X)
setup (hdX)
``` (hint: if you don't know what drive to set root/setup to you can press TAB at "root (hd" and grub will list all your drives). type "quit" to leave the grub console.

now you can shutdown your system and remove your ide drives and change your boot drive to "scsi" or "sata" in the bios. try to boot into your ubuntu installation. if the system boots make sure everything is where it belongs.

now look again if everything is correct and ALL your data is there before you at alst install your ide drives again and reformat/repartition them with gparted or qtparted.

---

### Post by isaiah55 on 2007-04-02
Thanks andi.

That mostly worked and what didn't, pointed me in the right direction.
My main issues were with editing the menu.lst from the console and sorting out the grub.

However I was able to get around these issues by editing the menu.lst via the gui interface and editing the fstab file.

So all is now well and I have migrated my data across to the SATA drives so thank you very much for all your help.

Cheers

Isaiah55

---

