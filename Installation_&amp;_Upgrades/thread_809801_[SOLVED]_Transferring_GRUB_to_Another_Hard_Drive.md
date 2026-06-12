---
title: "[SOLVED] Transferring GRUB to Another Hard Drive"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by hitenshi on 2008-05-27
I just recently installed my computer in a dual boot setup with Windows XP and Ubuntu. My computer has two hard drives, an IDE onto which both OS's are installed, and a secondary SATA storage drive. For some reason, when I restarted my computer after installing Ubuntu, it wouldn't boot to the GRUB screen, but rather, go straight into XP. So, after some tinkering, I found out that if my computer booted from the secondary SATA drive first, GRUB would run. I could always work this way, but I want to transfer GRUB from the SATA to the IDE. I've tried taking a look at [this]("https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668") article, but the explanation it provides doesn't help me too much. I don't understand it very well... >.<

Can anyone tell me how I might be able to transfer GRUB from my SATA drive to the IDE? Thanks. ^.^

---

### Post by meierfra. on 2008-05-27
Open a terminal (Applications->Accessories->Terminal), type

```
sudo fdisk -l
```

and post the output.


Then I (or someone else) will be able to give you detailed instruction.

---

### Post by IgnorantGuru on 2008-05-27
There are two issues...  you want to put grub's boot code in the MBR of the IDE drive.  You also want to tell grub where its root partition is.  The desired root partition (on your IDE drive) must have grub's stage 1 files on it (/boot/grub).  If it doesn't you should be able to copy them there, or install grub using the OS.

This briefly explains how to tell grub what root partition to use and how to install grub to the MBR...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#How_To_Set_Grub.27s_Root_Partition](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#How_To_Set_Grub.27s_Root_Partition)

---

### Post by hitenshi on 2008-05-27
Well... this is what I got from "sudo fdisk -l"

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003990d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5006    40210663+   7  HPFS/NTFS
/dev/sda2            5007       10011    40202662+   5  Extended
/dev/sda5            5007        9800    38507773+  83  Linux
/dev/sda6            9801       10011     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071eb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    b  W95 FAT32

```

---

### Post by meierfra. on 2008-05-27
To install Grub to the MBR of the IDE drive, open a terminal and type

```
sudo grub
```
and then at the "grub>" prompt:

```
find /boot/grub/menu.lst
```
(the "l" is  a lowercase L)

This should return (hd0,4) or (hd1,4). 

If it returns "(hd0,4)"  type this at the "grub>" prompt

```
root (hd0,4)
setup (hd0)
quit
```

If it returns "(hd1,4)" type 

```
root (hd1,4)
setup (hd1)
quit
```

instead.


Next backup and open the file "/boot/grub/menu.lst" via


```

cd /boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst
```

Look for the line

#groot (hd1,4)

change it to

#groot (hd0,4)


Look for your Windows item:

title Windows XP (or something like that)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
.....


change  "root (hd1,0)" to "root (hd0,0)"

Delete the lines "map (hd0) (hd1)" and  "map (hd1) (hd0)"

Save the file.


In the terminal type

```
sudo update-grub
```


That's it. You should now be able to boot from your IDE-drive.

---

