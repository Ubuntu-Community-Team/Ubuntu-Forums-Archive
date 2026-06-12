---
title: "Not seeing new 2TB drives on Ubuntu 9.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ceejay on 2011-04-28
This is yet another "I can't see my new disk" thread - sorry, I've had a good look at others and have tried the obvious but I'm stuck.

I have a working Ubuntu 9.04 installation - 3 SATA drives, in a home made box on an Intel DG965WH mobo. It's been working well for a long time (which is why I've not felt the need to upgrade the OS) but I'm running out of disc space so I've just bought 2 new 2TB drives (Seagate ST2000DL003).

The board supports up to 6 drives - in fact in previous configs I have had 6 running before.

Now, however:
- the BIOS is seeing the new discs (so they are connected and powered)
- new block devices /dev/sdd and /dev/sde are being created, but I can't use them...
- gparted lists just the three old drives, not the two new ones, in its menus
- sudo fdisk /dev/sdd returns "Unable to read /dev/sdd"

I've tried disconnecting one of the drives - /dev/sde goes away as you'd expect but /dev/sdd still won't work

In the BIOS, I have tried different settings - "Legacy" and "Native", makes no difference

As far as I can see, 2TB shouldn't be too big to worry the OS.

I'm now out of ideas - any helpful suggestions out there?

TIA

---

### Post by slooksterpsv on 2011-04-28
The first thing I would do is check for any BIOS updates on the motherboard as sometimes the BIOS may need a patch to support drives larger than X GB.

Does the BIOS recognize the drives? I would also set mine in Native (AHCI) and not Legacy mode.

Do this, open up a terminal and type in:
```

gksudo fdisk -l

```
And post the output here if you could, thanks!

---

### Post by ceejay on 2011-04-28
Thanks for the quick response. As I said in my first post, the BIOS is recognising the new discs, and I already tried Legacy and Native modes, which is what is on offer.

As I write I am continuing to experiment: right now I have it down to just /dev/sda (so I can boot!) and one of the new discs, which is therefore /dev/sdb. "fdisk -l" returns no output at all.

"fdisk /dev/sdb" returns "Unable to open /dev/sdb"

TIA.

---

### Post by oldfred on 2011-04-28
It says they are the new faster drives.

The SATA [COLOR=DarkRed]6Gb/s[/COLOR] interface and 64MB cache maximize performance.

I know there were support issues with older versions, not sure where it is at now. Most users were just plugging into the 3GB/s ports on the motherboards instead of 6GB/s ports and older drives worked, but I do not know if the drive speed makes a difference or has to match the port, etc.

---

### Post by coffeecat on 2011-04-28
I believe these are advanced format (4k) drives. I wonder if that is the problem - or part of the problem. I believe the version of Gparted in 9.04 will have problems with these.

Try booting up with the 10.10 or 11.04 live CD and seeing if these newer versions of Ubuntu can see the drives. If they do, then it might be wise to consider upgrading at last. 9.04 has been unsupported for 6 months now, so it's becoming a security risk, if nothing else.

---

### Post by ceejay on 2011-04-28
@oldfred ... I just had a look to see if there were any jumpers I could set but no, there are no physical settings at all on these drives.

In the meantime I just moved my root drive and one of the new ones over to another box with a completely different mobo (Gigabyte GA-G31M) and got exactly the same results.

@coffeecat ... That looks like a good theory. As you say, all I need to make me upgrade is some crisis like this one! I will get myself a live CD and give it a go.

Many thanks for the helpful comments.

---

### Post by ceejay on 2011-04-28
Update - coffeecat, you were quite right. I downloaded a live CD for 11.04, booted off it and gparted saw the new drive straight away. Formatting right now!  Looks like I'll have to do the proper upgrade in the morning.

Hmmm, probably also a good time to switch my other machine over from Debian as that will doubtless have the same problem.

Funny how a simple capacity upgrade turns into such a big job!

Thanks anyway.

---

### Post by slooksterpsv on 2011-04-28
Good to know, I'll remember that information for later on; just noted it.

---

### Post by oldfred on 2011-04-28
You may want to review this info on newer drives.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

If not installing windows ever, you may want to consider gpt partitioning.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

---

### Post by coffeecat on 2011-04-29
> **ceejay said:**
> Update - coffeecat, you were quite right.

Well - right to suggest trying a later version of Ubuntu. Not necessarily right that the cause of the problem was the advanced format issue. :) Maybe it was a driver problem with an older kernel. Whatever, glad it's given you the impetus to upgrade. Good luck!

---

