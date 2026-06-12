---
title: "Ubuntu Installation failure [Checked other threads]"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by pkravster on 2012-01-13
Hi,

I recently got an error while booting Windows  7 on my Asus G73 that read "A disk read error has occured, press Crtl alt del to  restart"

This happened after a windows update so I don't think its my hard drive failing. I using factory restore on my laptop but it gave an error "WIMsetreference file 3 failed"

So I checked BIOS and saw that my hard drive was being detected.

I went on to use a Ubuntu LiveCD to install Ubuntu. The Ubuntu installer gets stuck in the first stages.

Using the LiveCD, I tried opening Gparted but it doesn't detect anything. I also used DiskUtility and it shows my 21GB recovery hard drive, a 125 GB unknown drive (This is my C drive), and a 325GB hard drive (D drive with data).

It won't let me see the files in any of them. When I try checking it says that "the daemon is being inhibted"

I don't really have money to buy a new hard drive and idk if that is even the problem.

Do you think my hard drive is done? I wouldn't mind just erasing all the data and just installing Ubuntu if possibe, but I want that to be my last resort.

I'm completely new at this type of stuff, so would erasing the partition somehow take out restrictions to allow me to install Ubuntu?

Thanks

---

### Post by darkod on 2012-01-13
The factory restore probably started the process and because it didn't finish it left the disk in a weird state. But lets hope it's not dead, just difficult to read.

Deleting everything and starting over should be easy, but as you said, lets leave that as last resort.

You can try reading the disk with fixparts or testdisk. The first program is used to fix errors in the partitions/partition table. The second for partitions recovery (and the data on them).

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk is a very good tool to recover partitions as they were and the data on them in most cases. But the results can sometimes be confusing because it can offer more than one option, for example a partition you had long time ago and deleted yourself.
The tutorial on the website is very good.

---

