---
title: "RAID 10 on 6.06 Server Ed HELP!!!"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by noobboob on 2007-05-18
ok basics: i'm a newbie... complete newbie... like worst than a retard newbie
here's what i've done:

1. installed ubuntu 6.06 server edition on my ide hd
2. installed the gnome gui on top of it 
3. in addition to my 40gb ide hd, i have 4 320gb (1.28tb) sata hd's connected to a fakeraid card, Addonics-brand-card running the silicon 3114 chip
4. installed the dmraid pkg 
5. configured the Addonics' raid controller's to RAID 10 via the card's bios, so my logic drive is ~640gb

how do i get ubuntu to recognize the 640gb RAID 10? i can access the 40gb ide b/c thats where the linux kernel is installed... but my RAID is not there.... the raid drives are like sda, sdb, sdc, sdd or something like that.  do i need to partition/format them? how do i do that? am i missing something?

*** disks manager sees all the disks and dmraid -r shows the RAID 10 (two drives are 0 and the other two are 1, stripped & mirrored as far as I can tell)... /dev/mapper only shows "control"

PLEASE HELP!!! :confused:

---

### Post by igloocentral on 2007-05-24
Have a look at my new [FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug). Attach your results in this thread.

---

