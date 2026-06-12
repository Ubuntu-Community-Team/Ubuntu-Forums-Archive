---
title: "Forgot to defrag Windows before creating Linux partition"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by CycTim on 2008-08-06
[FONT="Tahoma"]And now Windows won't boot.

I'm using an eeepc 1000h and thought it would be nice to keep the dual boot - I gave Windows 10 Gig using the partitioner on the installer...

Every piece of the Windows data is still on the machine, but of course, seems to be split over 4 partitions (hd0,0 hd0,1 hd0,2 and hd0,3). My Linux partition is hd0,4 , running Hardy Heron...

Is it worth trying to save Windows? or should I just do a fresh install (from a bootable USB)?

The other problem is that I can't mount usb drives - I even removed any refernces to the cd-rom in the /dev lists, as the tute I used said that would stop me having any trouble mounting devices...


Any help would be appreciated..

Tim..
[/FONT]

---

### Post by AnarchyCow on 2008-08-06
I have to admit, I've never heard of Windows getting split over multiple HDD's.
The only thing I could think of, is that when resizing the partition, maybe your Windows files are larger than 10GB total. I imagine that would cause problems.

I would sugges manually editing the partitions during installation, not using the guided partition helper. A lot of times, it can end up doing things you didn't know it was doing.

How I set mine up.
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16573   133122591    7  HPFS/NTFS
/dev/sda2           16574       23989    59569020   83  Linux
/dev/sda3           23990       24321     2666790   82  Linux swap / Solaris
```
Basicaly, I just resized my Windows NTFS partition.
And then created a Ext3 main partition, which is mounted to "/"
Then a swap of about 2GB, even though it never gets used.

---

### Post by ad_267 on 2008-08-06
If you've backed up most of your data or you can rescue it from in Ubuntu then it might be a good idea to reinstall Windows.

I can't imagine removing the cd-rom from /dev is a good idea though?

If it's not too much trouble to reinstall Windows then manually edit the partitions to create one for Ubuntu and a swap partition.

Once that's sorted out someone else can probably help with getting usb drives to work :)

---

