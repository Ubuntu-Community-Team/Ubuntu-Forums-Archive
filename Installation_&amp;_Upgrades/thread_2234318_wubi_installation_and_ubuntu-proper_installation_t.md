---
title: "wubi installation and ubuntu-proper installation together"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by dink123 on 2014-07-14
[COLOR=#333333][FONT=UbuntuRegular]I have installed ubuntu through wubi in my machine. Now I want to install ubuntu in the normal way (maybe through live CD or bootable pen) and I don't want to uninstall my wubi ubuntu at this moment (until I get the new ubuntu installed)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So finally what I want to have is Windows 7, ubuntu (wubi) and the ubuntu installed through the standard way. Will this configuration work?[/FONT][/COLOR]

---

### Post by LastDino on 2014-07-14
There shouldn't be any problems.
 
Wubi has been rendered absolute, it will be in your best interest to get rid off it.

---

### Post by ajgreeny on 2014-07-14
> **LastDino said:**
> There shouldn't be any problems.
 
Wubi has been rendered [COLOR=#ff0000]absolute[/COLOR], it will be in your best interest to get rid off it.
Interesting typo!

[COLOR=#ff0000]Obsolete[/COLOR] was what you meant?

---

### Post by LastDino on 2014-07-14
> **ajgreeny said:**
> Interesting typo!

[COLOR=#ff0000]Obsolete[/COLOR] was what you meant?

Yes, indeed, thanks for correction ;)

---

### Post by sudodus on 2014-07-14
There are also these wiki pages about migrating wubi to a regular installed system

[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by oldfred on 2014-07-14
One of the major issues with most Windows 7 systems is that all 4 primary partitions are used. You have to free up one partition to become an extended partition and then can make as many logical partitions as you want or need.

Be sure to make good backups of all data. And best to have a Windows repairCD or Flash drive.
Shrink Windows using Windows partition tools and reboot immediately to let it run chkdsk and make repairs to its new size. But do not create partitions with Windows as it may try to convert to dynamic partitions which do not work with Linux and even do not work with some Windows tools.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by dink123 on 2014-07-16
Thanks guys I'll update if something goes wrong here.

---

