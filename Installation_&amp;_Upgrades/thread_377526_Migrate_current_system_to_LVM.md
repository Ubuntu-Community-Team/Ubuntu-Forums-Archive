---
title: "Migrate current system to LVM"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by El_Matthews on 2007-03-06
Gents,


I have two discs in my system;hda&hdb
one is used for windows and the other one for Linux.

the windows disk has some space free and I am going to schrink it. The free space that I get with this action should be added to my linux disk.

How do I start this ?
should I convert my linux disk to LVM to be able to expand it on an other phisical disk? If yes, how do I do this without loosing data (or reinstalling)?


All help appreciated.

---

### Post by El_Matthews on 2007-03-06
Gents,


I have two discs in my system;hda&hdb
one is used for windows and the other one for Linux.

the windows disk has some space free and I am going to schrink it. The free space that I get with this action should be added to my linux disk.

How do I start this ?
should I convert my linux disk to LVM to be able to expand it on an other phisical disk? If yes, how do I do this without loosing data (or reinstalling)?


All help appreciated.

---

### Post by El_Matthews on 2007-03-06
sorry posted this two times please see the other thread

---

### Post by El_Matthews on 2007-03-08
> **El_Matthews said:**
> sorry posted this two times please see the other thread

[http://www.ubuntuforums.org/showthread.php?t=377529&highlight=migrate+LVM](http://www.ubuntuforums.org/showthread.php?t=377529&highlight=migrate+LVM)

---

### Post by bapoumba on 2007-03-09
Threads merged ;)

---

### Post by El_Matthews on 2007-03-13
Gents


Any idea would be very appreciated. I am not asking a complete procedure in detail but a way of working. 

Maybe this can't be done and I should do a backup and restore, if this is the best solution do I simple copy everything to an other location. Reinstall kernel + LVM, next re-copy everything to my pc.

Greetings

---

### Post by erikcw on 2007-04-20
I'm trynig to figure this out myself.  Did you ever find an answer?  I don't want to have to wipe my whole disk to setup LVM.

---

### Post by El_Matthews on 2007-04-23
Hello erikcw,


I never had a response on this but I think the only way to achieve this is a backup and restore. If there is an other way I am not aware of it.

[LIST]
Backup everything[/LIST]
[LIST]Reinstall with LVM (this creates a partition /boot and a volume, the kernel etc will be installed in this separate boot partition).[/LIST]
[LIST]restore everything except /boot[/LIST]

---

### Post by erikcw on 2007-04-23
I actually figured it out, but haven't had a chance to post back.

I'm working on writing up a HowTo here:
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

Hope this helps!

---

