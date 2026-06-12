---
title: "USB startup disk creation without persistence in Ubuntu 16.04"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by marciomj on 2016-05-16
Hi, all!

I'm not sure if this is the right place to ask this, but I have a little curiosity about a change I've saw in the last release of Ubuntu.

The option to create a persistence space inside the USB disk creator was removed, and I would like to know why.

I've already searched for this info, but didn't find any answer.

Ubuntu 15.10

[IMG]http://postimg.org/image/4if96uehd/[/IMG]

[URL="http://postimg.org/image/4if96uehd/"]http://postimg.org/image/4if96uehd/
[/URL]
Ubuntu 16.04

[IMG]http://postimg.org/image/7q1tkao5t/[/IMG]

[http://postimg.org/image/7q1tkao5t/](http://postimg.org/image/7q1tkao5t/)

Thx!

---

### Post by PaulW2U on 2016-05-16
I don't have a definitive answer for you but this thread - [Select a tool to create USB boot drives to replace the Startup Disk Creator](http://ubuntuforums.org/showthread.php?t=2291946) - started some discussion with the Ubuntu developers about including a suitable USB creation tool in the next version Ubuntu, i.e. 16.04.

I seem to remember that there were so many bugs in Startup Disk Creator that it was decided to simplify what SDC could do. Ubuntu needed a reliable application to create USB images and SDC was, at the time, failing miserably.

---

### Post by marciomj on 2016-05-16
Thanks ,PaulW2U!

From this point of view, that option removal really make sense (althought I was one of the persistence fans).

I will take a look at that thread.

---

### Post by sudodus on 2016-05-16
The version of the Startup Disk Creator in Ubuntu 16.04 LTS ***clones*** the iso file, while previous versions copied parts of it, added a bootloader and did some editing. The details of booting have been changing between versions, which causes problems with the old version, while cloning the iso file is a robust process. The partition table and file system is read-only (the ISO 9660 file system for CD and DVD disks), so it will not work with a file or partition for persistence in the same drive.

There are other tools, that provide persistence, so if you want it, you can get it with mkusb and unetbootin (to mention two tools that provide persistence).

---

### Post by marciomj on 2016-05-16
Ok, sudodus. Think I get it.

Persistence isn't exactly a killer feature for me, but I have some using cases for it (mostly, maintain .txt files with some notes inside the Live USB).

I will try something with unetbootin, sometime in near future.

Thanks for explaining. :grin:

---

