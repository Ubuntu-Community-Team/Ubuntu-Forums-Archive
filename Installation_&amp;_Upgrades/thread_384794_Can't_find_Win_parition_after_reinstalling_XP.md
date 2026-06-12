---
title: "Can't find Win parition after reinstalling XP"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by carleton on 2007-03-14
So until recently I have been dual booting Edgy and WinXP without any trouble. I usually go weeks at a time without booting XP but this morning I decided I would reinstall XP because I had some work coming up I needed it for. 

The install went fine. Afterwards I of course had the usual problem of not being able to load GRUB or my linux partition, but I was pretty much expecting that. I booted up a live CD and reinstalled GRUB with the following steps:

```


sudo -i
grub
find /boot/grub/stage1 // Will print something like (hd0,1)
root (hd0,1)
setup (hd0)
quit
```

afterwards I could not load either partitions and started to worry. After poking around a bit I was able to get my linux partition working again by playing around in GRUB, but the windows has had no such luck, I can't even seem to find it from the Edgy Desktop I'm now running, and I'm a bit worried.

If anyone could offer any assistance, or direct me to post that can I'd really appreciate it. 

Oh and I'm using SATA drives, I'm not sure if that matters.

Thanks so much,

Carl
PS- Sorry for the typos in the title!

---

### Post by Kateikyoushi on 2007-03-14
Show us the output of this command.
```
sudo fdisk -l
```

---

### Post by carleton on 2007-03-14
Here you go:

```
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               7        9118    73192140    7  HPFS/NTFS
/dev/sda2   *        9119        9693     4618687+  83  Linux
/dev/sda3            9694        9726      265072+   5  Extended
/dev/sda4            9694        9726      265041   82  Linux swap / Solaris
/dev/sda5            9694        9694           0+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   c  W95 FAT32 (LBA)

```

thanks

---

### Post by Kateikyoushi on 2007-03-15
The good thing is that your partition is still there but probably not mounted, it is the sda1 partition.

You can mount it by following these steps. [LINK]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows")

I gladly help in case you need more assistance, then please post the output of the following commands.

```
ls /media
cat /etc/fstab
```

---

### Post by carleton on 2007-03-15
Thanks for your help, that link had everything in it I needed. I'm dual booting again with so much ease.

---

