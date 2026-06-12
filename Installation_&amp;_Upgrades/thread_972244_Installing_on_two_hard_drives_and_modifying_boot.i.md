---
title: "Installing on two hard drives and modifying boot.ini"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by plaxeb on 2008-11-05
I need some help. I dont want to play with master-slave connections on hard drive so i want to know is there easy other way to handle this installation of xp and ubuntu? I want to install xp on smaller (now master) hard drive and ubuntu on bigger hard drive. Do i have to use boot.ini modify or is there another way to make this doubleboot system wihouth changing master-slave rules?
Could someone post they boot.ini here as example?

---

### Post by Partyboi2 on 2008-11-06
Ubuntu uses grub as its boot loader which can handle multiple operating systems. I would suggest using rather then the windows boot loader. Did you install windows or ubuntu first? If you installed windows second you will need to restore grub which you can do by following [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

