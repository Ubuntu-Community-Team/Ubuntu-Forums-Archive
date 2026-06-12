---
title: "How to Install Ubuntu 10.04 without formatting drive D."
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by zer0svaughn on 2010-07-15
hey guys, I need your help.. I want to install Ubuntu 10.04 on drive C, i'm a newbie when it comes to installation.. my files are on drive D.. so i don't want to format drive D during the installation of Ubuntu.. please assist me guys.. thanks..

---

### Post by stlsaint on 2010-07-15
You dont have to format your D drive at all. You dont even have to touch it. Now i hope you are referring to two seperate drives and not partitions! So if you are using two different drives than yes you dont have to touch drive D. Just partition of some space on drive C and install ubuntu there.

---

### Post by mörgæs on 2010-07-15
A couple of defrags in Windows is a good step before installing, and remember to leave enough empty space for Windows when partitioning.

---

### Post by zer0svaughn on 2010-07-16
for example look at my attachment.. if i erase and use entire disk, will it only be drive C that will be erased? or drive D will be erased too?

---

### Post by gordintoronto on 2010-07-16
The right end of the line which begins SCSI3, is a drop-down arrow. Click it, and if you have two hard drives, the second one will appear there.

By the way, Drive C and Drive D are MS-DOS terminology. In Linux, drives have names such as hda or sdb. When there's a number, (hda1) it refers to a partition.

---

### Post by viralmeme on 2010-07-16
> **zer0svaughn said:**
> for example look at my attachment.. if i erase and use entire disk, will it only be drive C that will be erased? or drive D will be erased too?

It looks like you are using VMware virtual disks, which is a `feature' of Windows 7. You best bet is to resize this `disk' using the Windows utility and then install Linux in the newly created space. Before that, could you post a screenshot of your current partition setup?

[resize Windows 7 partition]("http://www.partition-tool.com/resource/resize-partition-windows-7.htm")

[resize virtual partition]("http://www.partition-tool.com/resource/resize-virtual-hard-disk.htm")

---

