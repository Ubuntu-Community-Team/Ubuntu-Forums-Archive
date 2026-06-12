---
title: "dual boot with Toshiba Recovery and Application Drive"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by haapsalu_sall on 2011-04-21
I tried unsuccessfully to install what I thought was windows in a virtualbox. After a ton of reading, I realized I don't actually have windows, but the Toshiba recovery discs that have windows on them. I was initially able to run Mint within Windows, but what I would rather do until I can buy windows (bleh) is dual boot. Will this recovery software allow me to partition the hard drive?

---

### Post by oldfred on 2011-04-21
Do you still have windows installed? Generally the recovery software has an image of the drive as purchased. Most let you create both a repair CD and recovery DVDs which you should do.

You can use Windows MMC to shrink the windows partition but do not use it for any additional partitions as it may want to convert partitions from basic to dyanmic which does not work with anything.

Some examples of installs and issues with 10.10:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by haapsalu_sall on 2011-04-21
I'm a little lost, but haven't read through all the links. I don' have windows installed anymore. Can I find Windows on the Toshiba recovery DVD and make an image of that?

---

### Post by oldfred on 2011-04-21
A windows boot loader and setting the recovery partition's boot flag may let your boot that. But it will erase your entire drive and all data on it. It will be back to the day you purchased it.

You may be able to boot with Supergrub also, not sure.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

