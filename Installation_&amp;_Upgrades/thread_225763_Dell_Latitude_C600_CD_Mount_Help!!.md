---
title: "Dell Latitude C600 CD Mount Help!!"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by crazycraig16 on 2006-07-30
Hi there I am running Dapper with my Dell Latitude laptop and I am having problems "mounting" my CD ROM Drive It says "Unable To Mount Volume" whenever I double click it, can anyone please help??

---

### Post by orb9220 on 2006-07-30
you need to open a terminal and in it copy and paste next line into term.

gksudo gedit /etc/fstab

and copy and paste your device list and post here so others can help.

---

### Post by wolfsandwich on 2007-08-03
i'm having the same problem with feisty 7.04 on a latitude c600  with my cdrw/dvd.

my results from the above command are:

(in the terminal)


$ gksudo gedit /etc/fstab
(gedit:5568): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.




(and in the fstab window)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=19d4a54c-8610-4b1f-b97a-bc9d478c7827 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=98b5d8ea-fd63-4027-925a-cb7b1dc78ad6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



any help greatly appreciated.

thanks.

---

### Post by wolfsandwich on 2007-08-11
got a new drive, problem solved.

thanks.

---

