---
title: "Ubuntu install 9.10 / 10.4 nohard drive partitions in partition editor"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by spoolboyy on 2010-05-01
Hey Guys,

I've never bumped into this issue before.  I'm working with an older PC that belongs to my parents.  They've been using Ubuntu 8.04 with no problems, and with 10.4s release, I planned to upgrade them to the newest version.

The system's specs are as follows:

1.5ghz Athlon XP CPU
1.5gb RAM (PC 2700)
20gb hdd (IDE)

I have tried both the Ubuntu 9.10 (two different discs) and a 10.4 install CD and both give me the same issue.  The installation proceeds along swimmingly until partitioning comes up.

The partition table simply shows no hard drives.  I have heard of this issue occuring with SATA drives and motherboard settings, but what could make it happen to an old IDE drive?  Any odd-ball motherboard settings or anything that might need to be changed?

GParted and the Live disc (along with the currently installed version of Ubuntu) recognize drives and can navigate them.  What gives?

Thanks in advance!


-Adam

---

### Post by cemartins on 2010-05-08
I have the exact same problem here.
I tried repartitioning and formatting the hd with GParted and I also tried switching the IDE plug it connects to on the motherboard. No luck

---

### Post by cemartins on 2010-05-09
SOLVED
I was able to install 10.04 using the alternate installation CD.

---

### Post by darkod on 2010-05-09
Not showing a disk in 9.10 and later is usually because of RAID settings on the drive. It was probably used as raid disk by you or previously.

If this is the issue, to remove the settings completely (if not running RAID of course), boot the live desktop and in terminal:

sudo dmraid -r -E /dev/sda (or the name of the disk if other)
sudo apt-get remove dmraid

If this was the problem there should be a question whether you want settings removed. After that the installer should work just fine.

---

### Post by VarianX on 2010-09-03
Just wanted to say thank you Darkod, this worked perfectly for me.

Anyone having a problem with the AV8 Deluxe motherboard (with a SATA Hard Drive) -- Darkod's post fixed my problem and the partition showed up!

---

