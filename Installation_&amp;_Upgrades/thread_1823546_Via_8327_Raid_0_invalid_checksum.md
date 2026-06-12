---
title: "Via 8327 Raid 0 invalid checksum"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by badbod on 2011-08-12
[LEFT]Hi,
 I am trying to install Unbuntu 11.04 on a Via raid 0. I have windows already setup and it boots fine, but Ubuntu does not see the raid set. Running dmraid -ay  (or any valid switch with dmraid) returns :

 sudo dmraid -ay -v
ERROR: via: invalid checksum on /dev/sdb
ERROR: via: invalid checksum on /dev/sda
no raid disks

mainboard is Asus M2V, with 2x Hitachi 250Gb disks in raid 0 configuration set in BIOS. 

I have a 3rd hard disk on the onboard Marvell 88SE6121 sata controller but this is not seen at all by Ubuntu either. I was thinking of installing it here if Ubuntu does not work the RAID, but no go it would seem.

I do remember installing an earlier version of ubuntu on this very same board using RAID 0 (2x 80Gb drives at that time) and the RAID was reconised and worked fine straight from live cd to full install.

Any ideas anyone?

[/LEFT]

---

### Post by steve11911 on 2011-08-13
This thread may help:

[http://ubuntuforums.org/showthread.php?t=1694018](http://ubuntuforums.org/showthread.php?t=1694018)

---

### Post by badbod on 2011-12-05
Hi,
 Sadly not, but thanks anyways. Is it a problem with dmraid?  the raid set works fine and I boot into windows with it. As I said beforeI did have it working in a previous version of ubuntu. Was recognized and worked straight away from live cd before. Now all I get is these damn 'invalid checksum messages'

I tried destroying the array and recreating it, tried different block sizes etc, just cant get it to work in linux at all. But works fine in windoze.

maybe report it as a bug with the dmraid guys?

---

### Post by badbod on 2011-12-05
I came across this [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) and it looks like it has the answer but I am struggling with it.

I get no files using 'dmraid -rD' so attached is the output of dd after following the instructions for '"dmraid -rD" generates no files'. This is from /dev/sda , I also dumped /dev/sdb and have almost identical data for the last couple sectors.

I'm afraid I wasn't smart enough to work out how to modify the via.h file myself so would be most grateful if someone could help me. 

In the via.h i see
```

#define	VIA_CONFIGOFFSET	((di->sectors - 1) << 9)
#define	VIA_DATAOFFSET		0

```

now if the metadata is not corrupt (works in windoze)then I am guessing I have to play with one of these 2 lines. Else My metadat does not match what is expected later in this file then I am really lost, I don't know anything about the metadata structure and google has not been helpful with this one.

Regards

---

### Post by darkod on 2011-12-05
Have you tried to use the alternate cd which is the recommended way to install raid? It might offer more chip support.

And for the third disk that is not even seen, does only the ubuntu installer not see it or also if you try fdisk -l it's not seen?

---

### Post by badbod on 2011-12-05
Hi Darkod,
 Yes I have tried alternate, server and desktop.

It is looking more and more like I will need to edit the via.h in the dmraid source as my metadata does not pass checksum for some reason. I am wondering if I can bypass the checksum altogether and see if my raid is then detected, though I would prefer to find why the checksum fails and patch it. The via v-raid utility in windoze gives the array a clean bill of health. Also that it used to work in Ubuntu 8.04 (I think it was ver 8.04 anyway) makes me think the dmraid is at fault and not my metadata.


The 3rd disk I am not bothered about. Ubuntu is simply not recognizing the marvell sata raid controller this main-board uses for sata ports 3 and 4. I have to install drivers in windoze 7 for it to work too, so this is not really a problem.

many thanks for your suggestions though, please keep em coming.

Regards

---

### Post by badbod on 2011-12-05
does anyone know which version of dmraid was in Ubuntu 8.04?

current ver : 1.0.0.rc16 (2009.09.16) shared

strikes me I just need to use the via.h from that version and it might work?

I could just go back through the versions of dmraid compiling and trying, but if the version is the same then I don't need to waste the time. 


Regards

---

