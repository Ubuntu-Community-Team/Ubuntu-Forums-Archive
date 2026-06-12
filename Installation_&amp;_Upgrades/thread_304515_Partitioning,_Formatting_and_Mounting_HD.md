---
title: "Partitioning, Formatting and Mounting HD"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by iecltd on 2006-11-21
I am totally new to Linux and ubuntu. Installation went well and I have an operating system,However I have a second hard drive which is not partioned or formated. I can see it as hdb in the system.when I look at its properties they are correct but create is greyed out. when I try to used fdisk under terminal it cannot access the disc for for that matter the main HD. I thought this may be due to not being logged on as administrator, however administrator is not a user and my current user name rodney is in the administrator group anyway. Can anyone help me?

---

### Post by mssever on 2006-11-22
Did you try ```
sudo fdisk /dev/hdb
```In Linux, the administrative user is called root. In Ubuntu, the root account is disabled by default because it isn't wise to log in as root. If you prefix a command with sudo (gksudo for graphical apps), you'll get root privileges.

You might find that installing gparted will make your life easier. ```
sudo aptitude install gparted
``` It will show up in System > Administration > Gnome Partition Editor.

---

### Post by iecltd on 2006-11-22
Thanks,

That let me use fdisk and I installed gnome partition editor however all command are greyed out as if I dont have the correct permissions? how do I use these commands?

I create a simgle partition with fdisk but got a swap partion which I have now deleted before I tried to use gnome partion editor.

---

### Post by mssever on 2006-11-22
> **iecltd said:**
> Thanks,

That let me use fdisk and I installed gnome partition editor however all command are greyed out as if I dont have the correct permissions? how do I use these commands?

I create a simgle partition with fdisk but got a swap partion which I have now deleted before I tried to use gnome partion editor.

It might be because the system is booted. I'm not sure. I like to use the gparted liveCD (google it), which you boot into and is the safest way to play with partitions.

When using fdisk, be sure to set the correct type (hit t). Use code 83 for Linux partitions.

---

### Post by iecltd on 2006-11-22
Thanks,
it seems I can do things in Fdisk so Ill progress down that path.

---

