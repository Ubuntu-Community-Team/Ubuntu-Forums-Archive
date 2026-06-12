---
title: "[SOLVED] XP, Hardy, Studio Triple Boot"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Belak on 2008-02-26
I recently tried something new. A triple boot. I haven't tried this before, so I figured it would be a good time to learn (seeing as I just bought a new 160 gb hd). Before I installed it, I backed up my XP partition by copying it to my external hd in a new folder. I tried the installation multiple times and eventually settled on the following partitioning (after screwing it up multiple times because of the stupid bios 137 GB limit):

1-ext3-hardy install (12 GB)
2-ext3 -studio install (12 GB)
3-ntfs-xp install (29.5 GB)
4-extended (rest of drive)
-5-ext3-hardy /home (12 GB)
-6-ext3-studio /home (12 GB)
-7-ntfs-general storage (80 GB)
-8-swap-swap (2.5 GB)

And I've got both Linux installs working, but the Windows partition refuses to boot. Is it because it was on the first partition and now it's on the 3rd? I tried the hide the first 2 partitions with grub, but it didn't work and now I get an error 17. Do I need to install windows on the first partition, or is there a work around? I'm just sick of reinstalling these OS's so I'm asking for help before I install again (I've installed 3 times on a new hard drive)

Oh, this might interest a few people... or help you help me:
Relevant part of /boot/grub/menu.lst
```
title		Microsoft Windows XP Home Edition
hide (hd0,0)
hide (hd0,1)
rootnoverify		(hd0,2)
savedefault
makeactive
chainloader	+1
```

Um, out put of sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042eb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1459    11719386   83  Linux
/dev/sda2            1460        2918    11719417+  83  Linux
/dev/sda3   *        2919        6505    28812577+   7  HPFS/NTFS
/dev/sda4            6506       19457   104036940    5  Extended
/dev/sda5            6506        7964    11719386   83  Linux
/dev/sda6            7965        9423    11719386   83  Linux
/dev/sda7            9424       19153    78156193+   7  HPFS/NTFS
/dev/sda8           19154       19457     2441848+  82  Linux swap / Solaris

```

Thanks,
Belak

---

### Post by wolfen69 on 2008-02-26
try making xp (hd0,0)

---

### Post by Belak on 2008-02-26
So, basicly I have to reformat my drive and try installing everything again?

I want to be sure this'll work because it takes a LONG time

---

### Post by wolfen69 on 2008-02-26
no, i meant change it to (hd0,0) in /grub/menu.lst

---

### Post by wolfen69 on 2008-02-26
> I want to be sure this'll work because it takes a LONG time

when i first started i used to just re-install everytime something screwed up, and there's nothing wrong with that. installing is an art that is underestimated imho. but the only way to get good at installing is to do it. make mistakes and move on, learn from it. nobody stops making mistakes. just have fun with it and learn. 

sorry, got sidetracked.

---

### Post by Belak on 2008-02-27
Well, I've installed so many times already. I like the alternate installer better than the LiveCD...

Anyway, I guess I'll try reformating my HD with the gparted live CD (again) then reinstalling (also again) and post here on how it goes.

---

### Post by Belak on 2008-03-02
It's easiest to just re-install windows... just be sure it's on the first partition if you want it to be drive C...

This can be closed now... thanks.

---

