---
title: "Language support NOT working and weird HHD format"
date: 2021-04-28
forum: Installation &amp; Upgrades
---

### Post by diablogamer on 2021-04-28
Hi there, this is my very first steps on Linux/Ubuntu and so far .... not so good.

I did a fresh install from scratch of Ubuntu and I already have problems. Hardware wise, everything is OK but I can't add a second language for my keyboard and I couldn't install Wine (that part is being taken care by the guys at Wine). Alos, I've done a fresh install so how come I see a FAT from windows and there seems to be some partitions not showing or missing. Very weird.
[B]
My version of Ubuntu:[/B]
```
me@Computer:~$ lsb_release -cs
focal
me@Computer:~$ 

```

OS NAME: Ubuntu 20.04.2 LTS
OS TYPE: 64-bit
GNOME VERSION: 3.36.8
Windows system: X11
x

**1) LANGUAGE**
As mentioned, I did a FRESH install of Ubuntu on this computer. The hardware seems to be OK and I can connect to the network (cable, WiFi all good). I installed Ubuntu in English and followed all the steps. Then I tried to add the French keyboard but it's impossible!
- setings works
- Language and region panel shows on the screen
But that's it. When I click on Manage Installed Languages the language windows appears and disappear so fats that I had to click several time on Manage Ins. Lang. to figue out what was the title of the panel showing for less than half a second. So I;m unable to make any written document in French.

- It's a fresh install
- Libre Office downloaded and installed right after
- Tried to install wine, but it got stuck (checking with the guys at wine atm).
- IMPORTANT: I tried to add the french keyboard PRIOR installing Libre Office and Wine and it didn;t work.

2) HDD
I installed Ubuntu and allowed to erase everything and to do a wipe of the empty space. I then checked the partitions I see few weird things.
- There's a FAT partition: 537MB at the begining
- There are partitions 2 and 5, but no 3 and 4

Can someone tell me if it's normal or not and if not how to fix that. I plan to have this computer on Ubuntu only, no dual boot. I'll use wine to play Diablo 2 tho.
I'm attaching a screen capture for the HDD[ATTACH=CONFIG]288385[/ATTACH]

Thanks for the help!

---

### Post by The Cog on 2021-04-28
HDD:
This looks normal to me.
The disk has an msdos style partition table. This kind of partition table only allows for up to 4 partitions. It always describes 4 partitions, whether or not they are actually used.

Partition 1 is the EFI bootloader partition. You will notice that this is mounted at /boot/efi. Don't mess with the bootloader partition.

Partition 2 is an "Extended" partition, which fills the rest of the disk. This type of partition acts as a container for other partitions, and is commonly used to allow having more than 4 partitions on an msdos style disk.

Partitions 3 and 4 would be the other two msdos-style partitions, but in this case we are not using them.

Partitions 5 and 6 are "logical" partitions inside partition 2. Probably Linux bootloader and encrypted data. It is normal to put these inside the extended partition, for the freedom to have more partitions and to resize them more easily if required.

---

### Post by diablogamer on 2021-04-28
Cog: Woof woof woof-woof wooof, waouf weouf-wiouf, wooooof.
Translation: Thanks for the info, I now feel reassured about this. Cheers! ... errr I mean: Woooooooof! ;)

---

### Post by diablogamer on 2021-04-28
Now if anyone can help with the language thing it'd be awesome.

---

