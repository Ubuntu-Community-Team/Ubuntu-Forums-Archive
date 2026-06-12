---
title: "is it dangerus to try to install a new operating system, and help installing one"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by dragonnutds on 2010-01-07
i am completly new to installing operating systems, i want to duel run both windows and Linux, but if something goes wrong, i don't have any of the original windows discs, can i lose windows, or is there a way to make a new windows installers.

---

### Post by oldos2er on 2010-01-07
If there's no data on your hard disk(s) that you want to keep, you can simply install Ubuntu using the entire disk. However, it would probably be best if you had a Windows restore CD, just in case.

---

### Post by dragonnutds on 2010-01-07
the hard drive is not blank, and i have none of the cds that came with the system, is there any way to make the windows restore disk, so i can keep windows if things go wrong.

---

### Post by howefield on 2010-01-07
Learn how to clone your disk.

Clonezilla for instance will do what you want.

Problem being that it is likely to be beyond you if you are as green as you say. Maybe best to have some one who knows beside you.

---

### Post by Sef on 2010-01-07
> Clonezilla for instance will do what you want.I would recommend [Clonezilla]("http://clonezilla.org/").  I am going to try it use it in the next few days after I partition my external hard drive.

> Problem being that it is likely to be beyond you if you are as green as you say. Maybe best to have some one who knows beside you.Experts would recommend backing it up before dual booting.   Everyone incurs problems at times.

---

### Post by kansasnoob on 2010-01-07
> **dragonnutds said:**
> i am completly new to installing operating systems, i want to duel run both windows and Linux, but if something goes wrong, i don't have any of the original windows discs, can i lose windows, or is there a way to make a new windows installers.

You don't say what version of Windows but these are great first time dual boot guides:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Of course when it comes to Windows you should always defrag first and it's always wise to back up everything!

---

### Post by kansasnoob on 2010-01-07
Oh, and always try running the Live CD first! Maybe your system won't like Ubuntu!

---

### Post by dragonnutds on 2010-01-07
thank you for the help, i will look into Clonezilla for my computer, but would it double as a backup?

---

### Post by howefield on 2010-01-07
> **dragonnutds said:**
> thank you for the help, i will look into Clonezilla for my computer, but would it double as a backup?

Using Clonezilla to image your drive will give you the ability to restore your hard disk back to the position it was in when you took the image. So yes, in that respect, it could double as a backup.

However, in addition to imaging your hard disk, I would also recommend backing your files and documents to a seperate disk, memory stick, cd, whatever for easy access.

---

### Post by dragonnutds on 2010-01-07
i was planning on saving the output of clonezilla to a separate disk, would that work?

---

### Post by lisati on 2010-01-07
> **dragonnutds said:**
> the hard drive is not blank, and i have none of the cds that came with the system, is there any way to make the windows restore disk, so i can keep windows if things go wrong.
Some Windows installations come with "recovery partitions" and software that will help make a set of recovery disks. The revoery disks act as a kind of backup for the operating system only, and you will have to find out ways of making backups of your important data. Tools such as the previously mentioned "clonezilla" can help with this task.
> **dragonnutds said:**
> i was planning on saving the output of clonezilla to a separate disk, would that work?
I've never used clonezilla, but, based on "general know-how" suspect that it might. Another option is to have a second hard-disk to which you copy your important data manually.

---

### Post by audiomick on 2010-01-07
What hasn't been said yet:
There is always a residual danger that something can go wrong, so all of the previous suggestions are good and valid.

Don't forget, though that the Ubuntu installer assumes that a lot of users are wanting to do a dual boot, and accommodates this. You should take all the suggested precautions, but you don't need to be scared of the installation. ;)

---

### Post by dragonnutds on 2010-01-08
ok, one last question before i think i am ready to start, is the recovery partitions protected from corruption? and thank you to everyone that is helping me, i really appreciate it.

---

### Post by audiomick on 2010-01-08
NO.
I would be really sure I know what is where, before I do anything.

Maybe boot into the live CD, start system> administration> gparted
and just have a look around before you start the installation. That will give you a clue how your HDD is set up, what is where, and prepare you for the partitioning step in the install.

If it is just a matter of installing next to windows, the installer will do that almost alone. If you want to keep some other partitions, e.g. a recovery partition, I think the best way is to choose manual at the partitioning step of the install.

There is good info about partitioning here:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You might want to set up your partitions before you start to install.

How you deal with the windows partition depends a bit on which windows. I _think_ it is ok to re-size an XP partition with gparted, but I _think_ it is better to re-size a Vista or Win7 partition with the windows tool. In any case, do your backups, throw out anything redundant on the windows install, de-frag at least once, maybe twice. Do the resize and re-start the windows a couple of times to see if it is happy and give it a chance to run it's file repair stuff if it wants to. Then do your install.

---

