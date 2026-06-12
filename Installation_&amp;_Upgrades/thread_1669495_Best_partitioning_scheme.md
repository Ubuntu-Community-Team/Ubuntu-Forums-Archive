---
title: "Best partitioning scheme"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by nubnux on 2011-01-17
Hi,

I'm wondering if someone could tell me what the best partitioning scheme could be for a 250gb hd. I decided to delete win7 and just go with Ubuntu so I'm not going to do a dual-boot. I tried to figure it out myself but it's kind of confusing with all the /, /home. /swap etc. partitions-mount points. I'd be really grateful if someone could help. Thanks in advance.

---

### Post by Bucky Ball on 2011-01-17
/ = OS, 20Gb plenty
/home = your personal data and settings, big as you like
/swap = 2Gb or 4Gb if you intend to hibernate.

All of these partition names are default names you can choose in the manual partitioning section of the install. You can add whatever other partitions you like to this, named whatever, but you will have /music, /video, /documents, /downloads, etc folders in your /home partition automatically.

Make 'em all EXT4 (swap takes care of itself) and go for 10.04 LTS as it is stable and long term support release; you will get a smoother ride for the moment. 

;)

---

### Post by nubnux on 2011-01-17
Thanks a lot. Though which partitions have to be primary and which logical?

---

### Post by Bucky Ball on 2011-01-17
Ubuntu will exist happily inside an extended partition on a logical. As long as you have no more than four primary partitions on a single physical drive or three primary and an extended with as many logicals inside as you like you are fine.

---

### Post by srs5694 on 2011-01-18
> **Bucky Ball said:**
> /swap = 2Gb or 4Gb if you intend to hibernate.

Actually, for hibernation, the swap partition needs to be at least as big as your computer's RAM size, so this value could be 512 MiB, 2 GiB, 4 GiB, 8 GiB, or many other things. Making it a bit bigger won't hurt, and is in fact advisable because of inconsistent use of units (MiB vs. MB, GiB vs. GB).

Also, a minor technical nit: It's "swap", not "/swap". The leading slash when referring to /home and various other partitions is a filesystem path indicator. Swap partitions, however, are not mounted -- you don't access them as /swap. Thus, there's no need for a leading slash, and adding one is incorrect from an English language point of view.

---

### Post by presence1960 on 2011-01-18
There is no "best" partitioning scheme. What is "best" for you depends on your needs and how many disks you have. I have 3 disks:

250 GB SATA: windows 7 sda1, Clonezilla installed on sda2, my mozilla profiles on sda3, extended sda4 with 10.10, 10.04 and swap.

500 GB SATA: one partition sdb1 with label Data for my data. No automount which would be /data in mount point on install.

1 TB SATA: 2 partitions split equally- one for my movies & video and the other as a backup of Data. Backups done with rsync.

You have to give it some thought and figure out a scheme that will make it easy for you to be able to do what you want to do on your machine.

srs5694 is correct about swap. If you want to hibernate you need at a minimum the size of your installed RAM for swap because if you have many windows and processes going and your RAM is almost or at capacity all that info will be copied to swap so you can hibernate and then resume where you left off.

---

### Post by nubnux on 2011-01-21
Thx for the replies guys. I installed it yesterday and so far I'm getting used to it pretty well, though I may have screwd up a bit. I failed to read about the "swap" and "/swap" difference. I did put /swap instead of swap at the swap partition I was supposed to make. Is the slash automatically fixed by the setup? But if not does it cause any problems now, which hopefully are fixable?

EDIT:

I think I fixed it. Can anyone tell me if this is a fine partition scheme, with swap working as it should?

[IMG]http://img84.imageshack.us/img84/6572/partitions.png[/IMG]

---

### Post by Bucky Ball on 2011-01-21
Yep, all good. Probably didn't need the / partition that big but no matter. You can easily resize if you really want to but I wouldn't bother. Nice job. ;)

If you need to

---

### Post by presence1960 on 2011-01-21
> **nubnux said:**
> Thx for the replies guys. I installed it yesterday and so far I'm getting used to it pretty well, though I may have screwd up a bit. I failed to read about the "swap" and "/swap" difference. I did put /swap instead of swap at the swap partition I was supposed to make. Is the slash automatically fixed by the setup? But if not does it cause any problems now, which hopefully are fixable?

EDIT:

I think I fixed it. Can anyone tell me if this is a fine partition scheme, with swap working as it should?

[IMG]http://img84.imageshack.us/img84/6572/partitions.png[/IMG]

Well done. Enjoy ubuntu!

---

### Post by srs5694 on 2011-01-21
> **nubnux said:**
> Thx for the replies guys. I installed it yesterday and so far I'm getting used to it pretty well, though I may have screwd up a bit. I failed to read about the "swap" and "/swap" difference. I did put /swap instead of swap at the swap partition I was supposed to make. Is the slash automatically fixed by the setup? But if not does it cause any problems now, which hopefully are fixable?

Don't worry about it. That was probably just the name embedded within the swap space, which isn't used for much. It can be used to refer to the swap space by name, but Ubuntu doesn't do this by default; and even if it did, it shouldn't cause any problems. You could call your swap space "fred" and it'd still work fine.

---

