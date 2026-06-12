---
title: "Install 8.04 and keep HOME?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Shin_Gouki2501 on 2008-04-26
Hello is it possible to install ubuntu 8.04 and keep the home while  overwriting the rest?
Im Runnning currently 7.04 Xubuntu and i simply want to keep my HOME. 
Is this possible? If so how?
I'm just downloading the hardy DVD i hope i can do that using the DVD.

---

### Post by SnakeHips on 2008-04-26
You should be ok but as always take a backup of home first.....then

Assuming you are comfortable around setting up partitions...

during install when you get to the partition bit (select "manual") you could setup as follows ,I did and found all my home stuff ready and waiting :-)

/
/swap
/home

for now lets take a look at your existing setup

from terminal post output

```
mount
```

---

### Post by Shin_Gouki2501 on 2008-04-26
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sde5 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sde6 on /media/disk-1 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

i think hda1 is the important one?!

---

### Post by SnakeHips on 2008-04-26
Ok looks like you took a guided install and everything is under one partition. /dev/hda1 on / type ext3 (rw,errors=remount-ro)

I would move your existing /home before the new install ,see this guide 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I can see you have two vfat partitions ,do you dual-boot windows?

---

### Post by Shin_Gouki2501 on 2008-04-26
those are simply from my external USB HDD

So you basically recommend me to put all my home stuff to a seperate partition. And if i install hardy i point the new /home towards this and it will not be overwritten?

---

### Post by SnakeHips on 2008-04-26
> **Shin_Gouki2501 said:**
> those are simply from my external USB HDD

So you basically recommend me to put all my home stuff to a seperate partition. And if i install hardy i point the new /home towards this and it will not be overwritten?

Yes ,*move* it as per the guide ,if you create the separate partition then it will look like this

current:
/
/home

run "mount" again to ensure you know the location of the /home partition - something like /dev/hda3

moving on to the new install and with a manual partition setup as i described in post2 your new setup can be configured as thus

/ 
format this and create new partition (ext3) say 10gig
/swap
create new - usually around twice your RAM
/home
dont touch this but make sure the mount point reads /home and not /media/blahblah


hope it helps

---

### Post by Shin_Gouki2501 on 2008-04-26
i have done all the backup stuff. tomorrow i will try the parition stuff!
thx so far i report if problems appear it "just" works ( as i hope) ;)

---

### Post by jajodo on 2008-04-26
This is a related issue.
I'm new to the forums and am not sure if I start a new thread or tie in with this.  Apologize if in error.

I upgraded from Gutsy to Hardy (clean install)
Previously had home on separate partition.
During installation I provided my user name and password and the upgrade recognized my files in home and incorporated my settings... perfect!

The problem is that the other 2 user accounts were not recognized.  When I attempted to add user I was prevented from using the same directory as that of the the existing files.
Tried as root and again was unable.  Ultimately deleted the directories (as root) and started from scratch.

Is there a better way to do this in the future?  Thanks.

---

### Post by gizmoarena on 2008-04-26
> **Shin_Gouki2501 said:**
> Hello is it possible to install ubuntu 8.04 and keep the home while  overwriting the rest?
Im Runnning currently 7.04 Xubuntu and i simply want to keep my HOME. 
Is this possible? If so how?
I'm just downloading the hardy DVD i hope i can do that using the DVD.


Why don't just copy the home directory somewhere else and then wipe out the whole thing?

---

### Post by SnakeHips on 2008-04-26
> **jajodo said:**
> This is a related issue.
I'm new to the forums and am not sure if I start a new thread or tie in with this.  Apologize if in error.

I upgraded from Gutsy to Hardy (clean install)
Previously had home on separate partition.
During installation I provided my user name and password and the upgrade recognized my files in home and incorporated my settings... perfect!

The problem is that the other 2 user accounts were not recognized.  When I attempted to add user I was prevented from using the same directory as that of the the existing files.
Tried as root and again was unable.  Ultimately deleted the directories (as root) and started from scratch.

Is there a better way to do this in the future?  Thanks.

Welcome! it's a good question ,sadly i'm not entirely sure of the answer but i reckon if you have a search around "user migration" or "import user account" - it may yield an answer.

---

### Post by Shin_Gouki2501 on 2008-04-27
> **gizmoarena said:**
> Why don't just copy the home directory somewhere else and then wipe out the whole thing?

Well my hope was that ubuntu actually did inlcude some comfort function to keep the home sutff, but seems it hasn't so i just start with partion stuff.

---

### Post by Shin_Gouki2501 on 2008-04-27
installation stuck at 95 %... ideas beside "try again"? -_-
i hate if that happens

---

### Post by Gina on 2008-04-27
If you install from the Live CD onto a new partition you get the chance to import the /home files (or My Documents in the case of Windows) from each other operating system on your computer.  If the account(s) is/are password protected you have to enter the username and password for each account you want to import - but it's all quite straightforward.  For some reason, the Alternate CD install doesn't seem to provide this facility.

---

