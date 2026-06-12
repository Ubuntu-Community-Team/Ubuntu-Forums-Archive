---
title: "Install problem"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by mdofl1 on 2007-06-19
Hi,

When I try to install 7.04 I get the following error message:  "The installer needs to commit changes to partition tables, but this cannot do so because partitions on the following mount points could not be unmounted:  /Media/New/040Volume"

Can someone help me with this please?

-C

---

### Post by dayhawk4 on 2007-06-19
It would seem that the disk that your trying to partition for installation of your new Ubuntu system is currently mounted.  If you type the mount command from any linux system without any parameters, it will give a list of different partitions which are currently mounted. So,

>mount

(Some list of mounted partitions

>

look for something in the list which has the beginnings of the list that won't unmount... for example

/dev/hda2 -t ext3 /new

This then would tell you that device hda2 is currently being used, and unless there is something further down the tree which is closer to your directory,(for example an entry like /dev/sda3 -t ext3 /new/media), then it will be hda1 which will be responsible for the trouble.  Knowing which partition is causing the problem is the first step in figuring a way around it.

Once you know which mount point is causing the problem, you will probably need to try and unmount it.  This you will need to do as an administrator.  In a regular linux installation, you will need to log into an adminstrative account, or start an adminstrative shell (a root shell, or log in as root user commonly).  Once you are here just type in the umount command together with the partition, something like:

>umount /dev/hda1

or alternately, you can type in the directory where it is mounted.  Something of the form

>umount /new/media

(If anyone sees some syntax which I've missed, I'm writting this from memory as I am working on upgrading my system currently as well.  Chime in and correct me as necessary.....)

if this unmounts the problem, you are ready to go.  If you have something on that partition that you need in order to complete the install, life is unfortunately more complicated.  Without knowing the layout of the system, where you are trying to install, what peripherials that you have, I am afraid that I can't be of much more help.  

Hope this is helpful,

      dayhawk4

---

### Post by dayhawk4 on 2007-06-19
excuse me, I said that hda1 would be responsible when in this example hda2 would be the responsible partition.  Ask questions if you need additional help.....

---

### Post by joshMigration on 2007-12-21
I'm having the same problem when I try to migrate from windows.  N00b here.  

[INDENT]"installer needs to commit changes to partition tables but cannot do so because partitions on the following mount points could not be unmounted:

/media/Part\040Two[/INDENT]

dayhawk4's solution involves having linux installed already.  what if I don't know what I'm doing and I need to take care of this problem using windows?

---

