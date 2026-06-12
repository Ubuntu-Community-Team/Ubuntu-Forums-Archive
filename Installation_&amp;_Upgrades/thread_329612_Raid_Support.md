---
title: "Raid Support?"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by capo on 2007-01-01
Hi. I have been struggling with Fedora Core 6 for weeks now and for some reason whenever i install onto a raid something goes wrong, even when i finaly manage to rebuild the array(s) and have everything 'working' for some reason i get absolutly abysmal! File System performance, like when i read from the HD my entire system locks up untill that read is done, and I/O is VERY slow. So what i want to know is does ubunut have the raid support i am looking for?

Basicaly can I?

Boot from the live cd, then use:

Fdisk to partition (i hate graphical partioners)
mdadm to set up and build the arrays.
And then install onto the arrays i build.

Will the ubuntu installer correctly pick up md divices i create with mdadm?

And just a general mdadm question, is it ok to create empty partiions with fdisk, then use them to build an md device (with mdadm), then format that md partition, but never actualy format the individual physical partitions before using them to build the md device?

Raid support is by FAR the most important feature i am looking for with AIGLX/GLX (compiz or beryl) as a distant second so this is very important to me. I dont want to format all my drives then find out the installer wont detect my MD deivces. Does ubuntu have any trouble with the /boot being on a raid 1. Any trouble with / being on a raid5, Is it ok to put the swap on a raid 0. Has anyone actualy tested these and installed ubuntu on a raid?

Thx in advance, capo.

EDIT: my hardware is the following:

Gigabye DS3
Core 2 e6400 @ 3.5ghz (under water)
7900GS @600/1.55 (under water)
2gb Of G.Skill HZ @ 876mhz, 4-4-4-12

and three 160GB seagate SATA disks.

---

### Post by capo on 2007-01-01
Ok so should i assume form the lack of replies that ubuntu has no raid support? Does it even have mdadm on the installer cd?

---

### Post by joebaker on 2007-01-02
The Alternate Install CD supports many advanced install options including Software RAID, LVM, other filesystems besides ext3, etc...

---

### Post by capo on 2007-01-02
ok well i am installing of that cd atm, but it hung for several hours after i created my raid and went back to the partitioning table, so i wne to bed. When i got back the table was there but one of the HD's had all the partitions missing, didn't even list any free space. I selected mounts points and formats for the raids anyway and went next but now it has been hung for over an hour on a blank blue screen with no text or anything. Though my HD active light is still going.. Are these extended hangs expected with the ubuntu installers.. seems odd,

---

### Post by DBEATTY on 2007-01-03
I have just completed a RAID 1 partition in Dapper Drake.

It was necessary for me to use a live "alternate install cd" which I downloaded from the University of Wisconsin (USA).

Help for this method is available here, [http://www.iki.fi.kuparine/comp/ubuntu/raid.html](http://www.iki.fi.kuparine/comp/ubuntu/raid.html)

Using the text install method I created three partions on each of two hardrives.

Kuparine's explaination is pretty good, but, I learned the hard way to create ext3 files and  /, swap and  /home  on the newly created RAID partions, not on the individual harddrive partitions ceated first.

(Trying to write ext3 and /, swap, /home on the 6 individual harddrive partitions causes the process to fail.)

Then write the changes to the RAID partions as indicated toward the bottom of the menu page. 

If you need further explaination, I will try to help.

---

### Post by Peturrr on 2007-01-14
Creating a raid array can also take quite a lot of time, and therefore the performance hit you describe could be that the raid array wasn't initialised fully yet. Therefore having very slow read/write performance.
A friend of mine had a 3 disc raid 5 array, with a performance of 3 mb/sec. After a lot of hours (3x 500GB drives) it suddenly went up to 100 mb/sec.
So, if your harddrive light shows their very busy, it is definitely initialising your raid.

---

