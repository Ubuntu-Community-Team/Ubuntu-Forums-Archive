---
title: "Ubuntu doesn't load"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by willyaranda on 2008-09-23
I had a problem and I needed to change the "primary" partition where Ubuntu was to a "logical" partition.

I had to change Grub to load Windows and Ubuntu and now, I can see the Ubuntu splash but the line that shows if it is charging only moves from left to right and rtoleft, but it doesn't change the OS itself.

My grub.list is (made with wifiway)

```
gfxmenu /boot/grub/message.wifiway
default = 0
timeout = 10
# Archivos de configuracion del GRUB  '/boot/grub/menu.lst'.
# Creado por  by 'hadrianweb' a dia de  mar 23 sep 2008 13:01:51 CEST
#
# La copia antigua de tu MBR esta en '/dev/hda' is
# here '/boot/grub/mbr.hda.4531'.  You can restore it like this.
# dd if=mbr.hda.4531 of=/dev/hda bs=512 count=1
#
# Comienzo de la seccion global del GRUB
#timeout 30
#color light-gray/blue black/light-gray
# End GRUB global section
# Other bootable partition config begins
  title Windows on (/dev/hda2)
  map (hd0,0) (hd0,1)
  map (hd0,1) (hd0,0)
  rootnoverify (hd0,1)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Comienzo de la configuracion del grub para wifiway-1.X

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

# Configuracion del grub para wifiway-1.x terminada 


```

Any help would be appreciated.

Thanks a lot!

---

### Post by Pumalite on 2008-09-23
Post:
sudo fdisk -lu
And if you can; a screenshot of Gparted

---

### Post by willyaranda on 2008-09-23
```
wifiway:~# fdisk -lu

Disco /dev/hda: 100.0 GB, 100030242816 bytes
255 cabezas, 63 sectores/pista, 12161 cilindros, 195371568 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1              63     8177084     4088511   12  Compaq diagnostics
/dev/hda2   *     8177085    90172844    40997880    7  HPFS/NTFS
/dev/hda3        90172845   195366464    52596810    f  W95 Ext'd (LBA)
/dev/hda5        90172908   191928554    50877823+  83  Linux
/dev/hda6       191928618   195366464     1718923+  82  Linux swap / Solaris

```

[[IMG]http://img223.imageshack.us/img223/2025/snapshot1ng5.th.png[/IMG]](http://img223.imageshack.us/my.php?image=snapshot1ng5.png)[[IMG]http://img223.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Pumalite on 2008-09-23
hda5 IS a logical partition. Get Super Grub and see if you can boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by willyaranda on 2008-09-24
I think I have some errors in my File System.

I'm doing right now a e2fsck -f -y /dev/hda5

Do you know how much time it will take to complete the task? Because I think there are lots of errors on inodes.

---

### Post by Pumalite on 2008-09-24
It takes a while.

---

### Post by collinp on 2008-09-24
^ Yes, it takes a long long long long time. You may not have Filesystem errors tho, since, from my understanding, you just installed. Grub may be somehow loading Ubuntu wrong or something.

---

### Post by willyaranda on 2008-09-24
hours? days?

it's a 50GB partition

can I stop it and continue in the future? thanks!!

---

