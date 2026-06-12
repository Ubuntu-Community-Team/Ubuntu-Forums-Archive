---
title: "Gusty and XP boot issue"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by ixlam on 2008-03-26
I have Gusty installed on SDA and XP in SDB.
I can boot gusty , but not XP .
Iadded entry into boot.list but booting XP just it  hangs at > " starting up ......"
If I disconect SDA XP boots just fine.

My menu.list

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=aac2543c-d9f0-46a3-aa62-7b8147d3b33e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=aac2543c-d9f0-46a3-aa62-7b8147d3b33e ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1


the output of my  fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123         608     3903795   83  Linux
/dev/sda3             609         730      979965   82  Linux swap / Solaris
/dev/sda4             731        9729    72284467+   5  Extended
/dev/sda5             731        9605    71288406   83  Linux
/dev/sda6            9606        9729      995998+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         319     2562336    7  HPFS/NTFS
/dev/sdb2             320        9728    75577792+   f  W95 Ext'd (LBA)
/dev/sdb5             320         450     1052226    7  HPFS/NTFS
/dev/sdb6             451        9728    74525503+   7  HPFS/NTFS


the Device.map is 
(hd0)	/dev/sda
(hd1)	/dev/sdb

can anyone help get them both to boot please?

---

### Post by Pumalite on 2008-03-26
Is Windows drive the priority boot in your BIOS?

---

### Post by ixlam on 2008-03-26
no .I believe SDA is primary boot drive
I  did however install windows AFTER Ubuntu..

---

### Post by Pumalite on 2008-03-26
Read this:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by ixlam on 2008-03-26
is there really no other way but to reinstall..
 both of the OS'es are there and functioning .. just cant get XP to start up from grub.
is there perhaps a command or parameter to add ?

---

### Post by dstew on 2008-03-26
Sometimes, XP doesn't like to be on the second disk. You can add map statements to the menu.lst file to fool it into thinking it is the first disk. See [this]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows"). Try:```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by ixlam on 2008-03-26
SOLVED ..
adding 

map (hd0) (hd1)
map (hd1) (hd0)

worked.... thank you for the help ..its been educational.

---

