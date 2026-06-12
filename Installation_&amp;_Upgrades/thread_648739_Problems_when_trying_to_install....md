---
title: "Problems when trying to install..."
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by dillonish on 2007-12-24
Hello, I am trying to install 7.10 on my new laptop, under a dual-boot environment.

But it hasn't worked yet, maybe something I'm doing wrong, but I get the feeling I might have screwed something up while messing around in Vista, which came Preinstalled on this machine.

FIrst let me tell you what error messages I'm getting...

I click Install, go all the way through past the keyboard layout selection, where it asks me Guided or Manual Partitioning. I've tried both.

Selecting Guided (the first option, I don't want to completely wipe my Vista install), I've tried plenty of resize options, everywhere from the default 57% to around 80%, same issue everytime, which I will post later (sorry if this is redundant).

Before I explain what I tried in Manual, let me say what I messed with in Vista (and hopefully didn't permanently damage). And I know this isn't Vista support, but whatever, some of the geniuses here might know what I did wrong. I was in the Disk Partitioning app that's included in the OS, I don't know the official name for it...
My Acer notebook had a preconfigured D: partition, which, I found out later, was for backups with the included software, probably a mistake deleting it. But I did anyway, removed that D: partition and stretched my C: to fill the empty space. Now there are two other partitions in there too on either end, labeled as EISA configurations or something, I was under the assumption that they held OEM images to build a factory reinstall disk, (useless to me now since the bundled software that used them got screwed up and kept crashing everytime I ran it, so I uninstalled it and now it will not reinstall).
ANYWAYS, I then tried to do a backup with that software and realized I needed that D: drive to do so... So I went back in, shrunk the C: drive, and eventually got another D: partition built, though it was only now labeled as a Logical Drive and under an "Extended Partition", which it definitely wasn't before. This is where I started realizing I screwed something up. Long story short, the bundled software kept crashing so I couldn't use it, so my new crappy D: partition became useless so I just let it sit, then my Vista install started messing up left and right and I started getting BSODs and things weren't recognized properly, etc etc, I'm an idiot for messing with things so important.

..
SO..
Under Ubuntu's Install/Partitioner/whatever, I then tried Manual. I tried Deleting that D: partition, and it seemed to turn to free space. I hit New Partition (ext3 or whatever) at the default size, and made that mount thing say "/" like the little thing down said to, or something. So it made that, I tried to install it on there but it said I needed a Swap Partition -_- (which the swap partition for vista is probably that last EISA on the end). So I tried to make one of those but, in short, I couldnt figure it out.
I then tried shrinking my C: again to make room for some new space, but that didn't work, gave me the usual error.

And that error, that I keep getting for everything, is:

[B]"RESIZE OPERATION FAILURE-
An error occurred while writing the changes to the storage devices.

The resize operation is aborted."[/B]
Button for OK, then it scans my disks and weirdly says no space is used on any partition, but after I hit Back it goes back to normal.

This error continues to occur.
I am worried, for a few reasons:
--Did I permanently screw something up with my MBR or something like that so my Hard Drive is corrupted and I can't repartition??
--Can I shut down this Ubuntu session on the LiveCD and still be able to boot back into Vista normally or have I deleted it accidentally by messing with things?
--The error usually seems to occur when resizing or editing the C: drive- are the files there unallocated or corrupted or messed up so it won't shrink or resize properly?

I'm so sorry to burden anyone with this problem, but I'm having a really foreboding feeling that I've genuinely ruined my laptop now :/

If I really really need to format my entire hard drive and just install this on it, I suppose I will, but I don't have any recovery materials for Vista, again because I'm an idiot.

Is there any hope?

I thank you for any help or insight you can provide.

-Dillon King

---

### Post by Sef on 2007-12-24
From the LIve CD > Applications > Accessories > Terminal

then type this command:

```
sudo fdisk -l
``` (Small L)

paste what it says in here.  


You need to shrink Vista with the partitioner that is provided with it.

Read [Psychocat's site]("http://www.psychocats.net/ubuntu/index.php").

---

### Post by dillonish on 2007-12-24
Sorry about the delay, slept in...

But here's what that command gave me:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8a66c15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       19122   143360000    6  FAT16
/dev/sda3           19122       23898    38366208    f  W95 Ext'd (LBA)
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics
/dev/sda5           19122       23898    38365184    7  HPFS/NTFS

```

Now should I try and shrink Vista within it, and if so, should I defrag it so it can shrink more or something?

Thanks, you've been very helpful.

---

### Post by dillonish on 2007-12-24
Still looking for help/recommendations on how I can partition this...

---

