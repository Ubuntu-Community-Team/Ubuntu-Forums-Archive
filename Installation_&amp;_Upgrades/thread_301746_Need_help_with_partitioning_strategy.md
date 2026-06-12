---
title: "Need help with partitioning strategy"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Jamie Jackson on 2006-11-17
I could use some help regarding a partitioning strategy for adding ubuntu edgy to my winxp laptop (dual boot). I'm a noob with just enough knowledge to be dangerous, so I need some validation and recommendations...

My internal drive:
[FONT="Courier New"]
Label Ltr Type  FS   Used/Capacity (Approximate)
Boot (C:) Basic NTFS    5/19GB
Apps (D:) Basic NTFS    7/15GB
Docs (E:) Basic NTFS   20/40GB
[/FONT]

Things I know:
[LIST]
[*]I know I'll want to share "Docs" between OSs.
[*]I'm going to free up ~20GB for new Linux partitions
[/LIST]

So...
1. Do I reformat [Docs] as fat32?
2. What's the best way to backup my current xp boot and apps partitions? (I'm assuming this is necessary.)
3. Does it matter what the order/location of the final partitions is? If so, what's the ideal?

Thanks,
Jamie

---

### Post by Irony on 2006-11-17
Well I tried the optimum partition set-up strategy quite a while ago - it consisted of 4 partitions... except that I now have 15 partitions.

The main partition you have to get right is the first one with windows in it, other than you might do ubuntu swap next then ubuntu root. fat32 can be used for windows and linux docs.

Anything after that you can do as you want because you can always alter them quite easily whether it is linux or ntfs or fat.

With linux installs you can even copy them from one partition to another. Say you have Ubuntu on hda3, you can simply copy it to hda5 (you don't have to reinstall) - you can't do that with windows installs.

You can have 4 primaries or 3 primaries and one extended partition. The extended partition can have as many partitions in it as you want.

---

### Post by Jamie Jackson on 2006-11-17
That's about the level of detail I need, thanks.

Also, I think I found the answer to my backup needs in [Partimage]("http://www.partimage.org/Download")

Thanks,
Jamie

---

### Post by Irony on 2006-11-18
See this for partimage use;

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Jamie Jackson on 2006-11-18
I'm all backed up, thanks.

Does this look like a sane approach, given 1GB of RAM? (I haven't applied the repartitioning yet.)

Before:
[[IMG]http://img230.imageshack.us/img230/2051/drivebeforerl2.th.png[/IMG]]("http://img230.imageshack.us/my.php?image=drivebeforerl2.png")

After:
[[IMG]http://img133.imageshack.us/img133/2761/driveafterot9.th.png[/IMG]]("http://img133.imageshack.us/my.php?image=driveafterot9.png")

Thanks again,
Jamie

---

### Post by aysiu on 2006-11-18
It's up to you, but I would read this little blurb about partition planning:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Irony on 2006-11-18
That's similar to mine except that my first 3 partitions are primary, hda4 encompasses the rest as logical partitions. Note that I Ided hda4 as W95 Ext'd (LBA) simply so that it shows up in Windows or else it looks like a blank space - other than that you can leave it as the default Id.

hda9 I use as my window/linux share;

[PHP]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1217     9775521    7  HPFS/NTFS
/dev/hda2            1218        1478     2096482+  82  Linux swap / Solaris
/dev/hda3            1479        2783    10482412+  83  Linux
/dev/hda4            2784       24792   176787292+   f  W95 Ext'd (LBA)
/dev/hda5            2784        4088    10482381   83  Linux
/dev/hda6            4089        5393    10482381   83  Linux
/dev/hda7            5394        6699    10490413+  83  Linux
/dev/hda8            6700        8004    10482381   83  Linux
/dev/hda9            8005        9310    10490413+   b  W95 FAT32
/dev/hda10           9311       10615    10482381   83  Linux
/dev/hda11          10616       11920    10482381   83  Linux
/dev/hda12          11921       13225    10482381   83  Linux[/PHP]

---

### Post by Jamie Jackson on 2006-11-18
> **aysiu said:**
> It's up to you, but I would read this little blurb about partition planning:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Interesting, though the author makes the seemingly unorthodox claim that the location of the swap doesn't make a real difference.

The FS-share/ext3 share drive idea is intriguing. Do you happen to know if there are any gotchas to this strategy?

---

### Post by Jamie Jackson on 2006-11-18
> **Irony said:**
> That's similar to mine except that my first 3 partitions are primary, hda4 encompasses the rest as logical partitions.

Whoops, I guess that's what I meant to do, too. I guess I wouldn't even be able to boot my Ubuntu if it weren't a primary. (Right?)

I'm going to go try to find/read a general partitioning primer, I stink at this.

---

### Post by Irony on 2006-11-18
It doesn't matter where Ubuntu is primary or logical it will boot.

It doesn't matter where swap is though I've seen it said that it is best at hda2 or before root, I've had it several places and it makes no difference.

You will also find you can use one swap for several distros.

---

### Post by Jamie Jackson on 2006-11-19
Okay, thanks for the info.

Man, am I glad I went through the trouble to backup. I left the laptop alone to go through it's repartitioning, and when I came back, the laptop had run out of power in the middle. (One of my kids must have tripped over the cord.) My drive was pretty hosed, but the partimage backups restored perfectly.

Now, I've got Ubuntu installed, but it's not booting to grub, but I'll start a new thread for that.

Thanks again,
Jamie

---

### Post by Bartender on 2006-11-19
Jamie -
Were you using the LiveCD to install?  To me, the place where you have the option to change GRUB's target is a little bit tricky.  If you manually partitioned, you already went thru the mapping part, then set out the mount points, then it looks like you're leaving the partitioning section.  

I was wondering about GRUB at that point; hadn't seen anything about where it was going to go.  There it was, on the last page before Ubuntu is ready to wreak havoc on your HDD...a little tiny box where you can change the target for GRUB.  It could be you missed it.  Or maybe you put it in the wrong place, like I did a few weeks ago before some of the guys on the forum helped me out.

---

### Post by Jamie Jackson on 2006-11-19
Hi Bartender,

Yeah, I was installing from the live dvd, and I did see the option to change the grub partition, but I guess I picked the wrong one. I chose (hd0,1), and I think I was supposed to choose (hd0,2).

I'll look for your forums posts and look at your solution.

Thanks,
Jamie

---

