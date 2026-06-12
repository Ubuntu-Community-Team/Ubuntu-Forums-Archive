---
title: "grub problem on edgy"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by calford on 2007-03-17
Hi,
I have 2 hds one for XP one for linux, just installed edgy and now it doent boot.
I noticed that if i unplug (no power) the windows drive the otherone boots normally, but if i have them both neither system boots from grub.

this is my configuration from fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6489    52122861    7  HPFS/NTFS
/dev/sda2            6490       24321   143235540    f  W95 Ext'd (LBA)
/dev/sda5            6490       19354   103338081    7  HPFS/NTFS
/dev/sda6           19355       24321    39897396    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40017485312 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4664    37463548+  83  Linux
/dev/sdb2            4665        4865     1614532+   5  Extended
/dev/sdb5            4665        4865     1614501   82  Linux swap / Solaris

and this is an extract of my menu.lst

title		Ubuntu, kernel 2.6.17-11-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash

initrd		/boot/initrd.img-2.6.17-11-generic

quiet

savedefault

boot

title Microsoft Windows XP Professional

root (hd1,0)

savedefault

makeactive

chainloader +1


any ideas??

thanks.

---

### Post by Kateikyoushi on 2007-03-17
Seems when you connect the windows drive the disc order changes, try changing data cables or port on motheboard maybe then it won't happen, if that's not a solution have to edit the grub menu.

You have to change the hd(0,0) to hd (1,0) in the linux entry and vice versa for windows then reboot with both drives plugged in, it should work.

---

### Post by calford on 2007-03-17
thanks for your reply Kateikyoushi

i cant switch the hdds because one is a SATA drive (windows, sda1) and the otherone is a PATA.

forgot to say, 
there is an extra file called device.map on the same folder as menu.lst with this info

(hd0) /dev/sda
(hd1) /dev/sdb

---

### Post by pradeepadapa on 2007-03-17
just tell the output which u get when u try these commands when u attach both the hdd's

from the live cd  sudo grub

grub>find /boot/grub/stage1

---

### Post by calford on 2007-03-17
grub> find /boot/grub/stage1
(hd0,0)
(hd2,0)

---

### Post by Kateikyoushi on 2007-03-17
First time I see a PATA drive as sda, might be the ide controller.

---

### Post by calford on 2007-03-17
its sharing the port with a DVD drive (master/slave).
I used to have drapper on the same configuration with no problems

---

### Post by calford on 2007-03-17
i guess the problem started when i unpluged the windows drive to install ubuntu. somehow grub is getting confused.
It cant be that hard to fix, can it?
or do i have to reinstall with the windows drive plugged?

---

### Post by calford on 2007-03-17
ok i managed to get windows working from GRUB
i did some mapping

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]

and now that one works, linux is still down. when i choose linux from the grub menu i can see the ubuntu logo and the loading bar but it freezes there.

That seems like another problem to me. after all it looks like it did find the hard drive where Linux is, but somehow couldnt load it

i had a look in my /dev/ folder and i dont have any hd? or sd? there, should it be like that? i noticed that grub points that way for the hard drives.

---

### Post by pradeepadapa on 2007-03-18
why dont u put (hd2,0) in menu.lst of grub and see whether it boots or not, or just at the recovery mode prompt press 'e' and change the boot line from (hd0,0) to (hd2,0) and boot in recovery mode.....

---

