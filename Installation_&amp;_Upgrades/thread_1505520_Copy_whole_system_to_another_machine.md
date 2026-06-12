---
title: "Copy whole system to another machine"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by tashe on 2010-06-09
Hi
I am fairly new to Ubuntu, I use it as my prime OS for 3 months now. 
I have set up on my machine an environment for development of software for my university assignments, like installed Java, database, eclipse and other stuff. Now I am going to be away from my computer for some time, and at that place I have a different PC which has nothing on it, not even Ubuntu.

I want to know if it is possible to copy the whole system as it is, with all the installations, files and stuff and install it on a different machine.
I am using Ubuntu 10.04.

Thank you,
Mite

---

### Post by presence1960 on 2010-06-09
Use [clonezilla]("http://clonezilla.org/")

---

### Post by darkod on 2010-06-09
Zdravo Mite. :)

Another interesting options seems to be this (the FS Archiver part):
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

If you don't mind working from the command line of the system rescue cd. It might even be better option for you if the partition(s) on the new computer will be smaller in size, but big enough to accept the data.

Clonezilla requires the target partition to be same size or bigger than the source partition. It least it says so on their website. With FS Archiver you can restore to smaller partition in size. It has to be big enough for the data of course.

---

### Post by tashe on 2010-06-09
Thanks guys (&#1041;&#1083;&#1072;&#1075;&#1086;&#1076;&#1072;&#1088;&#1072;&#1084; :D )

I'll try the Clonezilla program since it seems simpler and I don't have the problem with hard drive space.

---

### Post by konqueror7 on 2010-06-09
you could try using [Remastersys]("http://www.geekconnection.org/remastersys/index.html"):p

---

