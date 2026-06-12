---
title: "hard drive problems that MIGHT be solvable?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by nso on 2006-06-07
Hola! I have 2 hard drives on my computer. One running Windows and running Ubuntu. Though the diversity in these hard drives doesnt stop there. One is a SATA hard drive and the other is connected by IDE. I am having trouble in accessing the hard drive running windows from ubuntu though i set it as accessible through the disk manager i still recieve the error: [You do not have the permissions necessary to view the contents of "disks-conf-sda2".] while the ubuntu hard drive isnt even visible to me through explorer. Is the problem solvable at all? I'll post what ever is needed just give me the code.

---

### Post by Sutekh on 2006-06-07
- For accessing the Windows drive in Ubuntu you should read and follow the steps in this link

[http://psychocats.net/ubuntu/mountwindows.php]("http://psychocats.net/ubuntu/mountwindows.php")

_______________

 - For accessing the Ubuntu hard drive in Windows, you might want to consider
[URL="http://www.fs-driver.org/"]
FS Driver - Ext2 Installable File System For Windows[/URL]

---

### Post by nso on 2006-06-07
ty worked up until the fstab editting because all fstab pulls up are:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

but my windows partition is on: [ /dev/sda2

is there another code to put to pull up the sata drives?

---

### Post by Sutekh on 2006-06-07
[quote=nso]
but my windows partition is on: [ /dev/sda2

is there another code to put to pull up the sata drives?[/quote] You need to add a line for the /dev/sda2 partition to your fstab, its not automatic. The link shows you how to edit your fstab, it makes no difference what sort of drive it is.

---

### Post by nso on 2006-06-07
Thank you. It worked :grin:

---

