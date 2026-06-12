---
title: "Problems with Partitions"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by EsbenAndersen on 2010-12-26
Merry Christmas everybody! :)

I know this is an issue that's been tackled numerous times in other threads, but I haven't been able to find an answer to my specific problem. Hope someone can help.

The thing is I want to install Ubuntu alongside my Win 7 32-bit OS on its own partition. I have four partitions: System Reserved (made automatically by Win 7), System (where Win 7 is installed), Ubuntu (which is a partition I made during the installation of Win 7 that is empty) and data (where all my documents, music and such is at).

The problem is that when I get to the point in the installation of Ubuntu where you choose where to install it, Ubuntu doesn't recognize any partitions at all! So to install Ubuntu I would have to erase everything which I would very much like to avoid - moreover I read it was better to begin with installing Win 7.

If I choose to 'Try Ubuntu' and thereafter open GParted this is what it looks like:

[IMG]http://img812.imageshack.us/img812/263/gparted.png[/IMG]

The weird thing is that when I open 'Computer' I can see the different partitions and even open the partitions and files on them. It seems to work the way it should.

[IMG]http://img441.imageshack.us/img441/8218/computern.png[/IMG]

When I open a drive it creates a shortcut on the desktop. So when I've entered all of them it looks like this:

[IMG]http://img171.imageshack.us/img171/1852/desktopjt.png[/IMG]

This is how the partitions look like in Win 7:

[IMG]http://img593.imageshack.us/img593/7913/capturejyv.png[/IMG]

The reason why the Ubuntu drive is FAT32 is because I tried formatting the drive while in 'Try Ubuntu'-mode. It didn't work with NTFS either. The harddisk is a Samsung HM251JJ ATA.

So what is wrong? Why can't the Ubuntu installation read my partitions? There's even a partition ready for it. And as I wrote I have looked at a great deal of threads but can't find out what to do.

Hope someone can help, because I think Ubuntu is by far the greatest OS out there, and it is frustrating not to be able to use it.

Esben.

---

### Post by dino99 on 2010-12-26
Are these partitions all "primary" ? If so thats a bad scheme (max 4 primary partitions per device)

Mainly you have to use winblows tools to deal with it, and Ubuntu (Linux) tools to install ubuntu (Linux)

Follow the mini howto below & choose a manual installation (dont let the installer to make choice for you: you are the boss and you decide :))

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by EsbenAndersen on 2010-12-26
Will I have to delete my Win 7 and Data partitions in order to do this? It seems to my that to follow the steps I will have to 'start over'.

Esben.

---

### Post by dino99 on 2010-12-26
i suppose you might have free space inside each partitions, so you can resize them to get room. Then you can reorganize if you want/need.

Its a good idea to clean (defrag, remove old things, ....) first

---

### Post by efflandt on 2010-12-26
What is the output of **sudo fdisk -l** (small L).  You have not showed enough of the Windows window to see if you have normal partitions or logical volumes.  It is possible that Linux does not trust itself trying to modify proprietary Windows volumes, so it does not show that option.

---

### Post by CraigThomas on 2010-12-26
> **dino99 said:**
> Are these partitions all "primary" ? If so thats a bad scheme (max 4 primary partitions per device)

I'm no expert but what Dino says makes some sense.
Perhaps (if you have nothing in the Ubuntu partition) you could delete it from within Windows, then run the Ubuntu installer again and hopefully it will allow you to create the fourth partition as an extended partition and install Ubuntu there.

There's a reasonable concise explanation here:
[http://en.kioskea.net/contents/repar/partitio.php3]("http://en.kioskea.net/contents/repar/partitio.php3")

Hope it helps.

---

### Post by srs5694 on 2010-12-26
See [this Web page](http://www.rodsbooks.com/missing-parts/index.html) that I wrote about this problem. I can't guarantee that the cause is the same for you, but odds are good that it is. If that page doesn't help you, please post the output of:

```

sudo fdisk -lu

```

Type this in a Linux emergency disc boot or the Ubuntu installer's terminal in "live CD" mode. Note that's "-lu", not simply "-l" -- the "u" makes fdisk report values in terms of sectors rather than the much less precise cylinders; cylinder reporting is almost completely useless for diagnosing the cause of this problem.

Also, be sure to post the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. Failing to do this will unalign columns, making the output difficult to read and interpret.

---

### Post by EsbenAndersen on 2010-12-28
Checked BIOS. My HDD is set up for AHCI.

Then I ran the fdisk -lu command and here's the data that followed:

[IMG]http://img638.imageshack.us/img638/9095/fdisk.png[/IMG]

Thanks for the help so far guys!

---

### Post by srs5694 on 2010-12-28
It appears that the disk has leftover GUID Partition Table (GPT) data, which is confusing GParted (and other tools based on libparted). Perhaps you'd previously used the disk with a Mac, or experimented with GPT under Windows or Linux but switched to MBR using a utility that didn't know enough to wipe out the GPT data. You'll need to wipe out the errant GPT data. [This post](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34) of mine in another thread describes how to do this. There's a chance you'll need to re-install your boot loader after you do this; however, since the system only boots Windows at the moment, that seems unlikely. In any event, if you immediately install Ubuntu after wiping the GPT data, that will install a fresh copy of GRUB 2 (the standard Ubuntu boot loader).

---

### Post by EsbenAndersen on 2010-12-29
I'll try that.

Yet a question though. If I decide to start over by removing all partitions, install windows and then make a 'data' partition again, would that work too? Or should I expect the same issue?

Thank you so much for your help srs5694!

---

### Post by srs5694 on 2010-12-29
> **EsbenAndersen said:**
> If I decide to start over by removing all partitions, install windows and then make a 'data' partition again, would that work too? Or should I expect the same issue?

It depends on how you "start over." The issue is this: Primary MBR partitioning data appear in the first sector of the disk (aka the MBR, or sector 0). GPT includes a "protective MBR" in that first sector, along with data in the 33 sectors immediately following the MBR and in the last 33 sectors of the disk. MBR partitioning tools know nothing about these extra GPT data structures, and so tend to ignore them when you create a new partition table. Some tools, though, see them and become confused when they exist along with a non-protective MBR.

So, if you want to start over, you *must* do so with a GPT-aware tool, or manually wipe *both* the first 34 sectors of the disk and the last 33 sectors of the disk. Anything based on libparted will do; tell it to create a fresh MBR ("MSDOS partition table" is how most libparted-based tools refer to it, IIRC). Linux's fdisk will *not* do. My GPT fdisk (gdisk) that I refer to in the post to which I linked in my last post can wipe everything GPT-related, but I don't recommend using it to create new MBR partitions (it's primarily a tool for manipulating GPT data structures). I don't know what to recommend in the Windows world, since I'm less familiar with the Windows tools. I *suspect* that the Windows installer does a poor job of it, based on problem reports like yours; but I've not tested this in detail.

---

### Post by EsbenAndersen on 2011-01-03
Ok. I've decided to format the entire harddisk. A fresh start. So the question is - what is the best way to partition my harddrive when I want the following:

1: A partition for Win 7 32 bit.

2: A partition for Ubuntu 10.10 32 bit.

3. A partition for all my documents that can be accessed from both Win 7 and Ubuntu (I'm in particular in doubts regarding how to format this partition - NTFS, FAT32, one of Ubuntu's formats?).

Hope someone has experience with this.

Esben.

---

