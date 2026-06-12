---
title: "How can I ghost my mini ITX server?"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by jumpslu7 on 2008-06-07
I have a mini-ITX server that I'd like to upgrade the hard disk in.

I've currently got two 2.5" hard disks in there configured as a raid array, and I'd like to replace them with an 80Gb 3.5" SATA-II hard disk.

The mini-ITX box is ubuntu based, and acts as a webserver, database and DNS server for my internal network, and I really can't do without it for any length of time!

Moving the entire config over by hand would be an extremely labourious task and I was wondering if there were any other solutions.

Could I for example, ghost the mini-ITX box to a VMWare virtual machine on my workstation, then replace the new hard disk in the mini ITX box and copy the virtual machine back to the newly installed hard disk?

just thinking out loud there, I don't know if that's even possible.  All suggestions welcomed!

thanx!
[http://belfastgeek.net](http://belfastgeek.net)

---

### Post by quinnten83 on 2008-06-07
I have no clue how to help you, but if byghosting you mean create an image, you can try with clonezilla. I never managed to get it to work, but I think that is due to my not knowing how to work it.

---

### Post by mastermindg on 2008-06-07
Check out this link:

[Backup and Restore]("http://ubuntuforums.org/showthread.php?t=35087")

This is the simplest way to "ghost" a Linux install.

---

