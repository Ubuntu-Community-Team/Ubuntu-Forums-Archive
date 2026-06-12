---
title: "'Lost' swap after resizing partitions with GParted"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by adm1968 on 2010-01-07
[FONT="Georgia"]Used GParted to resize a couple of existing partitions. Once completed, the system was rebooted.
I do not seem to have a swap partition any more

My /etc/fstab file:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=815314cc-cd27-40da-8eb3-f22037e3b06f /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=53cebf81-3eda-46c9-ada7-81e428a170b5 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=5f5ae884-68d0-48da-8038-8069fef72186 /swap            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Anything looking wrong?
What could be the reason for this behaviour?
[/FONT]

---

### Post by adm1968 on 2010-01-08
[FONT="Georgia"]I did search before asking
Could anybody help?[/FONT]

---

### Post by audiomick on 2010-01-08
Hi.
the quickest thing might be to open
system> administration> system monitor (or something very like that. I have to translate out of German...)
and have a look on the third tab, "resources" how much swap the system is recognizing. The middle graphic is RAM and Swap related, the size of the swap space is visible underneath on the right.

If it is showing the same as what you expect, then all is ok.

If that is not ok, have a look here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
for some very helpful info about the state of your computer.

or, run
```
fdisk -lu
```
for a list of partitions

and
```
sudo blkid -c /dev/null
```
for the UUIDs.

With these results, you should be able to see if your fstab is looking in the right place.

---

### Post by adm1968 on 2010-01-08
[FONT="Georgia"]Thanks a lot. Will try that![/FONT]

---

### Post by adm1968 on 2010-01-10
[FONT="Georgia"]Great!
Everything working now
I combined your suggestion with something I managed to find in our forums

Thanks!:D[/FONT]

---

