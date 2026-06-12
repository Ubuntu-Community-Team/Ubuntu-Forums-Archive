---
title: "Can't boot XP from Grub"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by AriciU on 2007-11-04
I have XP and Ubuntu installed. I have 4 hard drives. 3 are SATA and 1 is IDE (windows).

/dev/sda = windows
/dev/sdb = ntfs partition
/dev/sdc = ntfs partition
/dev/sdd = ubuntu

Here's the deal. When i try to boot XP from grub's menu i get a "Waiting for..." ("Loading windows...") - forgot how it says it but it's not that important and windows should load. However, it doesn't, it just sits there waiting... for me to die of anger probably.

The funny thing is. If i put the XP install cd in the cd drive, reboot, don't press any key when it asks me if i want to boot from cd, Windows loads fine but Grub menu doesn't appear at all.

Menu.lst is pointing to windows fine. If i set it in any other way (hd1,1 ; hd2,2; etc) then i get an "invalid executable" error 13 witch means i'm pointing it to the wrong drive.

---

### Post by hal8000 on 2007-11-04
Post the output of
sufo fdisk -l

and

cat /boot/grub/menu.lst

---

### Post by AriciU on 2007-11-04
> Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069098

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61c1f1de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38782   311516383+   7  HPFS/NTFS
/dev/sdb3           38849       38913      514080   82  Linux swap / Solaris
/dev/sdb4           38783       38849      536760   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb64aa047

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      379445   191240248+   7  HPFS/NTFS
/dev/sdc2          381527      387621     3071849    f  W95 Ext'd (LBA)
/dev/sdc4          379446      381526     1048824   82  Linux swap / Solaris
/dev/sdc5          381527      387621     3071848+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb37ab37a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3187    25599546   83  Linux
/dev/sdd2            3188        6374    25599577+  83  Linux
/dev/sdd3            6375        9561    25599577+  83  Linux
/dev/sdd4            9562       48641   313910100   83  Linux


and

> title		Windows XP 
root	 	(hd3,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu
root		(hd2,3)
kernel		/ubuntu/vmlinuz26 root=/dev/sdd2 ro
initrd		/ubuntu/kernel26.img
quiet

---

### Post by meierfra on 2007-11-05
Try

title Windows XP
rootnoverify (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
savedefault
makeactive
chainloader +1

---

### Post by AriciU on 2007-11-06
I've got it fixed.

It was my damn motherboards secondary sata/raid controller. The drive on that controller would try to boot first regardless of the order i had set in the bios.

I've switched that drive to the regular controller and put another one (with no MBR) on that lame controller and after a few grub reinstalls and a bios update everything works fine now.

I even deleted the MBR from the sata drive witch would try to boot first (dd=/dev/zero bla bla), rebooted, grub was gone like it should but it was just sitting there instead of switching to my other drive to boot from.

Mental note of the day: Avoid motherboards with a SIL raid controller on them at all cost.

---

