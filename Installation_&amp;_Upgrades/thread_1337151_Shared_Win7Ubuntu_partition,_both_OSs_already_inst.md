---
title: "Shared Win7/Ubuntu partition, both OSs already installed"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by teachmeifyoucan on 2009-11-25
Hi,

my computer is set up with a 10gb Windows 7 partition, a 10gb Ubuntu 9.10 partition, about 160 gb of unpartitioned free space, and a 6gb Linux swap partition.

Both Windows 7 and Ubuntu 9.10 are already installed.

All of the how-to guides on shared partitions say that one should first install Windows on a clean system, use Windows to partition the drive, and only then install Ubuntu.

Well, I didn't do that.

Is there still some way to partition the 160gb of free space so that it can be accessed by both operating systems?

I tried formatting it as FAT32 with GParted, but Windows didn't recognize it. Strangely enough, GParted doesn't let me format it as NTFS. Some sources claim that FAT32 doesn't work for partitions that large.

So I then tried formatting it as NTFS with the Cute Partition Manager boot CD. But Windows didn't recognize that either.

In both cases, Windows Explorer shows me the Windows C: drive, the DVD D: drive, and an E: drive that cannot be accessed without formatting it. Windows is unable to tell me the size of this inaccessible drive, so I can't tell whether it's the 10gb containing Ubuntu, or the rest of it. This is why I'd rather not risk formatting it and having to reinstall Ubuntu all over again.

Any ideas? Thanks!

---

### Post by presence1960 on 2009-11-25
Did you use gparted Live CD? Get it [here]("http://gparted.sourceforge.net/livecd.php")

---

### Post by darkod on 2009-11-25
Windows would never show you ext3/ext4 partition as E:. It might actually be your 160GB partition.

What exactly does windows disk management tool show? Usually it would display the ubuntu partitions as a partition but no letters are assigned and it can't read the format at all. Not without additions to it.

PS. Just for reference, I am dual booting with Win7 and I have 2 ntfs partition and 3 ubuntu (/, swap and /home). The disk management tool is showing all of them and with correct sizes, but of course the ubuntu partitions have no letters assigned to them. In fact it does not even recognize that swap and /home are logical inside extended, so it is saying all 5 are primary which is impossible. :) So much for windows disk management.
In Computer I can see only my C: and D: and I don't even expect to see the linux partitions there.

---

### Post by teachmeifyoucan on 2009-11-25
Thanks, both of you, for your quick and helpful replies! The bootable version of GParted works like a charm, and your information on Windows behavior was spot-on.

---

### Post by coffeecat on 2009-11-25
I know the OP has now used Gparted live, but just a FYI for everyone posting here.

> **teachmeifyoucan said:**
> GParted doesn't let me format it as NTFS.

That sounds as though you were trying to create a NTFS partition from Gparted in a hard disc installation. For Gparted to be able to create and manipulate NTFS partitions, you need also to install the package ntfsprogs. The live Ubuntu CD comes with ntfsprogs which is why you can edit/create NTFS partitions using Gparted in the live CD, but ntfsprogs doesn't get included in a default install - even though it is on the CD.

Presumably Gparted live also has ntfsprogs.

---

### Post by darkod on 2009-11-25
> **coffeecat said:**
> The live Ubuntu CD comes with ntfsprogs which is why you can edit/create NTFS partitions using Gparted in the live CD, but ntfsprogs doesn't get included in a default install - even though it is on the CD.

Presumably Gparted live also has ntfsprogs.

One of my dilemmas resolved. I have also noticed it can't create/format ntfs. Thanks.

---

### Post by coffeecat on 2009-11-25
> **darkod said:**
> One of my dilemmas resolved. I have also noticed it can't create/format ntfs. Thanks.

See that dent in my forehead? It took ages for the penny to drop. :wink: Just glad to share to prevent others similar pain.

Also - there are a number of greyed-out filesystems in Partition > Format. There are a number of *utils or *progs packages in Synaptic which, if installed, will bring the entries to life. Handy if you have a sudden pressing need to create a hfs+ or xfs partition.

---

