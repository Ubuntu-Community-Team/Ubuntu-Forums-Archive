---
title: "big problem with ubuntu..."
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by caredudeu on 2007-05-05
okey so i've installed ubuntu to my computer and wantet to have dual boot with windows and ubuntu, but i didnt install ubuntu to a partision, just to my harddrive, and i cant boot into windows. I've been looking trough the forums for some time for some answers on how to fix this but i just can't seem to find any =\
plzzz help me here, i really just want to get em both working without having to reformat or anything, cause i got clot of stuff on my windows that i really need and can't be lost
i've also tryed to reinstall windows Xp but it says that the dics is damaged and can't install XP
and C-promt wont work eigher =\
so as you guys see i really need some help here :'(

---

### Post by Gerard Barberi on 2007-05-05
If you installed Ubuntu onto the same drive as Windows (without partitioning), then you have already formatted over your WinXP install.  In order to have both installed for dual booting, the two OSs have to be on separate partitions.  Try using the gparted live CD and follow this guide.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by caredudeu on 2007-05-05
so its all gone then... is there anyway i can get my stuff from windows, my files and stuff?

---

### Post by mikewhatever on 2007-05-05
Can you please post the output of the following from the Terminal (Applications>Accessories>Terminal)
> sudo fdisk -l

---

### Post by caredudeu on 2007-05-05
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
device      boot     start   end          blocks       id    system
/dev/sda1    *       1       11661        93666951     83    Linux
/dev/sda2            11662   12161        4016250       5    Extended
/dev/sda5            11662   12161        4016218+     82    Linux swap / Solaris

```

---

### Post by PolarisNexus on 2007-05-05
Yep, you formatted to the Linux filesystem on the whole of the drive.  Its not possible have both NTFS and EXT3 on one partition, so it looks as if you have lost your entire Windows information sorry.

What you MIGHT be able to do is, use a drive recovery program in linux to obtain the lost data that hopefully shouldn't have been overwriten.    But thats only if you did a quick format to EXT3...

---

### Post by caredudeu on 2007-05-05
got any good program for that? =\

---

