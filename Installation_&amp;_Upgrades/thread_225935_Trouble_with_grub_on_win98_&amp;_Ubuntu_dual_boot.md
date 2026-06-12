---
title: "Trouble with grub on win98 &amp; Ubuntu dual boot"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Germain Capde on 2006-07-30
Hi everyone,
this is my trouble:

I have a PC Pentium 3 - 733 MHz where win98 was installed. Then I have installed Ubuntu 5.10 on a new partition. All worked excellent and the partitions get like this in hd0:
hdc1 - win98
hdc2 - ubuntu
hdc3 - ext3
hdc5 - swap
(hdc because they are in secondary IDE , in primary i have cdrom and cdrom recorder - is it ok, it doesn´t matter?)

Everything was OK, so i decided to play a little and broke grub. What i´ve done was add an image to grub and when i reinstalled it i´ve made some mistake that installed grub not only in MBR, besides in win98 partition boot sector.
So when grub starts it works OK but win98 option goes back to grub start.
Ubuntu option works fine and ubuntu boots fine.
What i tried with no luck was:
- Reset MBR
With a:\fdisk /MBR with a floppy of win98 to boot PC.
Nothing changed.
I think in this case MBR points to win98 partition boot sector where Grub is copied so is the same problem.

- Reset win98 partition boot sector
In this case i boot with the win98 floppy and do a:\sys c: and the problem is that device c: returns error:
Abort, Ignore, Retry?
This may indicate that partition is wrong but from ubuntu i can mount it and it works properly.

Sorry for the large explanation but with this is enough for you to suffer for me and try to help me.

Bye,
German

---

