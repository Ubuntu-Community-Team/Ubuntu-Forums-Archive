---
title: "Help!!! partition problem"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by garrychnca on 2011-02-12
I have a 500GB disk with my laptop which now consists of:

1) (C: )volume with windows 7
2) SYSTEM volume
3) HP_TOOLS volume
4) RECOVERY (D: )volume

1 to 4 are originally there.

And now I shrink (C: )by 30GB to get a unallocated space in which I decide to install ubuntu.

Question is when I get into the ubuntu installation and it comes to the install-allocate drive space section of the installation, I have no idea how to deal with it.

I searched and they say I have to convert the unallocated space to an extended disk BUT I failed to do that in Windows7 by using the diskpart command in CMD.

**lol and i don't know why that my installation don't have the option of "install along-side with other operating system".....**

Can anyone help? I will really appreciate that!

This is the screen shot of my Disk Management:
[http://img828.imageshack.us/i/captureryn.png/](http://img828.imageshack.us/i/captureryn.png/)

[IMG]http://img828.imageshack.us/i/captureryn.png/[/IMG]

[IMG]http://img828.imageshack.us/i/captureryn.png/[/IMG]

---

### Post by srs5694 on 2011-02-12
You can thank HP for using up all four of the primary partitions on the disk, leaving you with none for expansion.

IMHO, the best solution is this:


[list=1]
[*]Boot Windows
[*]Locate the utility to burn a recovery DVD set and run this utility. This will create a set of DVDs that hold the contents of one of your partitions (probably your D: volume; it's normally about 10-20 GiB in size, IIRC). Run the utility a second time, since burned DVDs are less reliable than factory-pressed DVDs. While you're playing human disc changer, write a letter to HP (with a cc: to Microsoft) telling them what you think of their being so cheap as to not include proper recovery DVDs with the computer. They'll keep doing this sort of thing if people don't complain.
[*]Use the Windows partitioning tool to delete the partition that's just been rendered unnecessary by your creating the backup DVDs.
[*]Use the Windows partitioning tool to shrink your Windows C: partition by however much you want to shrink it. You may also want or need to move another partition, depending on their arrangement. The key is that you want all the free space to be in one big block.
[*]Reboot into the Ubuntu installer.
[*]Use the advanced (or "manual", or whatever it's called) partitioning option.
[*]Create an extended partition in the free space.
[*]Create a 5-20 GiB logical partition for Linux's root (/), a logical partition of 1-2 times your RAM size for swap space, and give the remaining space to a logical partition for /home.
[*]Proceed with a normal Ubuntu installation.
[/list]


There are many possible minor variants of this procedure, and some major ones, too -- for instance, some people consider the HP_TOOLS volume to be useless and so just delete it outright; or they back it up, delete it, and then restore it to a logical partition.

---

### Post by MVG-V70 on 2011-02-12
I have common problem on HP G62 notebook, but Ubuntu installer doesn't see any volumes on HDD.

---

### Post by srs5694 on 2011-02-12
> **MVG-V70 said:**
> I have common problem on HP G62 notebook, but Ubuntu installer doesn't see any volumes on HDD.

Please start your own thread for your own problems. Trying to resolve two peoples' problems in one thread becomes very confusing very quickly.

---

### Post by KingLewy on 2011-05-07
This helped me a lot. Thanks very much :)

---

