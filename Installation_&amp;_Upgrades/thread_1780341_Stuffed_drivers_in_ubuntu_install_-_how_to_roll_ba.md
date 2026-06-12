---
title: "Stuffed drivers in ubuntu install - how to roll back / install vanilla"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by intransit on 2011-06-11
Hi all,

During some messing around with my default ubuntu 10.10 install, I have totally destroyed my wireless drivers (the original ones worked, I can't even remember what I was trying to achieve) anyway, basically I have stuffed it so that wireless doesn't work anymore.

What is the easiest way to just rollback to a default install with normal drivers? I'm happy to upgrade to newest version 11.04 or whatever, if that makes it easier, but I'd like it to override my bastardisation and become vanilla install again...

Any ideas? Thanks for the help.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **intransit said:**
> Hi all,

During some messing around with my default ubuntu 10.10 install, I have totally destroyed my wireless drivers (the original ones worked, I can't even remember what I was trying to achieve) anyway, basically I have stuffed it so that wireless doesn't work anymore.

What is the easiest way to just rollback to a default install with normal drivers? I'm happy to upgrade to newest version 11.04 or whatever, if that makes it easier, but I'd like it to override my bastardisation and become vanilla install again...

Any ideas? Thanks for the help.

Don't use 11.04 unless you really really want to..  I tried it. Wasn't happy with the results since important drivers like printer drivers wouldn't work correctly anymore..

Stick with 10.10 and you can't go wrong:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Hopefully you did a backup.

---

### Post by intransit on 2011-06-11
Got nothing I need to keep on it - back up is no issue
I just wanna revert to vanilla. Except I am in a dual boot situation where windows was installed first, so usually I would just redo the isntallation but im not 100% how well it will work in this scenario - to just refresh the ubuntu side...

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **intransit said:**
> Got nothing I need to keep on it - back up is no issue
I just wanna revert to vanilla. Except I am in a dual boot situation where windows was installed first, so usually I would just redo the isntallation but im not 100% how well it will work in this scenario - to just refresh the ubuntu side...

Boot from the live Ubuntu 10.10. Use gparted to remove anything you don't want. Install Ubuntu 10.10. And follow the guide above. You should be fine. :)

---

### Post by intransit on 2011-06-12
ok so I am ready to go with this

I know what the partitions are and where I want to install it...

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       49531   396318444+   7  HPFS/NTFS
/dev/sda3           59332       60802    11805696   17  Hidden HPFS/NTFS
/dev/sda4           49531       59332    78725121    5  Extended
/dev/sda5           49531       58927    75471872   83  Linux
/dev/sda6           58927       59332     3252224   82  Linux swap / Solaris

well dunno what sda1 is I think it is a windows partition
sda2 is my main windows partition
sda3 I think is the vendor partition 
sda4 I dont know
sda5 the ubuntu partition I want to why
sda6 is ubuntu's swap

So I think i basically just want to format sda5 and reinsstall there. Thats fine. But when I use gparted or the "advanced" installation (shows partiton manager) it says to me no root filesystem is defined.
Fine ok, happy to define one, but what does that mean? which one SHOULD be my root filesytem ??? this is the root filesystem for ubuntu ? then I guess it will be sda5 ???

**Can anyone help me with just that bit ?**

I am pretty sure that is the root filesystem for ubuntu, and in which case, I should set it to dev/sda5, but would appreciate some feedback that my understanding is correct before I blindly hit the go button :)

Also do I need to put mount point as /windows for the windows partitions or just leave as is and just specify the / root filesystem ?

---

### Post by oldos2er on 2011-06-12
The root filesystem should be defined as /
When you have sda5 highlighted in gparted, there should be a drop-down menu that allows you to specify this.
Leave the Windows partitions alone.

---

