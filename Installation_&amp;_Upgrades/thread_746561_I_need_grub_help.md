---
title: "I need grub help"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Zyphrexi on 2008-04-05
I know I probably did something dumb while installing, depending on where grub was written, which I really don't know. hd0 or something.

I don't remember how to specify which /boot to ... boot.

I have two installs (three if you count vista, but that's on a separate drive)
7.10 which I'm on now, and 8.04 which doesn't come up in the boot list, rather when grub loads it looks to the 7.10 install for /boot/grub.conf 

now how do I write grub without messing up my mbr or whatever? I used to know this, but it's been a long time since I did an install like this.

---

### Post by mikewhatever on 2008-04-05
Post the output of <sudo fdisk -l> for the start. All this may need is a few lines added to grub menu file.

---

### Post by Zyphrexi on 2008-04-05
```
Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca4f7d63

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23175   186149856+   7  HPFS/NTFS
/dev/hdb2           23175       24322     9208832    7  HPFS/NTFS

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20448   164248528+  83  Linux
/dev/sda2           20449       48641   226460272+   5  Extended
/dev/sda5           47554       48641     8739328+  82  Linux swap / Solaris
/dev/sda6   *       20449       46465   208981489+  83  Linux
/dev/sda7           46466       47553     8739328+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

also I used this [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

and reinstalled grub to 1,5 (literally /dev/sda6) and ```
setup (hd0)
```

---

### Post by mikewhatever on 2008-04-06
So, is Hardy installed on sda1? I think you could add an entry for it to grub's menu. Can you post the outputs of the following: <ls /dev/disk/by-uuid -alh> and <ls /media/sda1/boot>. I've not used Hardy yet, but guess the entry should be similar to that of Gutsy, just different parameters.

---

