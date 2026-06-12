---
title: "Lost power during upgrade to 11.04"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by happyisland on 2011-10-26
My wife's laptop was causing her problems so I recommended she upgrade to 11.04 to see if that would help out. Unfortunately, most of the way through the upgrade process the computer lost power. 

Now when I try to browse the HDD with a live CD the only part of it that is available is the 240MB partition (and not the remainder of the 250GB HD where all the files are). 

It's looking grim - HELP!!!

Thanks in advance, HI

---

### Post by TBABill on 2011-10-26
Did you backup those files before starting the upgrade? If you did, just reinstall while connected to power and copy your files back into the fresh install. If you didn't, you'll hopefully get recommendations soon if others have experienced HDD failure (or failure to read) after upgrade or install.

---

### Post by happyisland on 2011-10-26
Unfortunately not. I know that was risky, and in retrospect I feel like an idiot, but I've done dozens of upgrades since I switched to Ubuntu in 2006 and I've never lost any data. I've always figured that no matter what happened I would be able to access my data using a live CD or similar approach. 

My wife is going to kill me.

---

### Post by happyisland on 2011-10-27
so now when I look at the disk in disk utility, using a live cd, the only mountable partition is the 240MB first partition. The remainder of the drive is listed as 'unallocated'. 

Does anyone know of any good tools for recovering the data (mostly my wife's family pictures) from this unallocated partition?

Thanks in advance,

HI

---

### Post by oldfred on 2011-10-27
If you can mount the partition run filechecks, as any power failure often leaves a partition in an unstable state.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

You can also try testdisk & photorec.  Testdisk will try to find partition(s) and may show file system. If do that is really good. If not photorec will scan drive for files that look like a file. I had saved a text file many times & it found every version as each save was written to another location on drive as it was not very full. Not sure I ever found the last saved version. It does not find file names, but music & photos have internal data you can use to regenerate some naming.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

---

### Post by happyisland on 2011-10-27
Thanks for the fantastically helpful post, Oldfred! Much obliged. I'm now going to follow your instructions.

Saludos from Aruba!

---

### Post by happyisland on 2011-10-27
So now I'm able to use an ubuntu live cd to see the messed up partition with photorec. Looks promising! 

Here's the thing now: I'd like to backup the photorec output onto my attached usb drive. That drive is visible in the photorec list as being located at /dev/sdb. Problem is, it is listed as RO (I'm guessing that means 'read only') and I can't select it as an option for a place to output the files. What gives? Any quick help on this would make my day, night, week, and month.

Thanks in advance,

HI

---

### Post by oldfred on 2011-10-27
Is usb drive partitioned? You should be seeing sdb1, sdb2 etc. What format is partition(s)?
```

sudo fdisk -lu
```Then it depends on how you mount it. I tought defaults were read/write but they have been changing. NTFS often is not read/write by default.

Mounting:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

