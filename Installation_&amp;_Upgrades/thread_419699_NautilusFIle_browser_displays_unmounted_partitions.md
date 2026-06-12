---
title: "Nautilus/FIle browser displays unmounted partitions"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by raidensix on 2007-04-23
Hi,

I just installed Fesity and I noticed that the Nautilus File Browser is also displaying partitions that are not mounted. Is there anyway to not display unmounted file systems ? 
One FS is the windows C drive which I rather not have visible and the other is an ext3 that I
do not want to use at the moment, They were initially not listed in the fstab file but nautilus still displays them even when I added them to the fstab with noauto.

Anyone have any ideas ?

---

### Post by pt78 on 2007-04-24
I'm having the same problem :(

---

### Post by leg on 2007-04-24
I quite like that feature.

---

### Post by raidensix on 2007-04-24
Found a work around in another thread. I mounted them to a hidden folder and that fixed it for me.

---

### Post by pt78 on 2007-04-25
Hi, 
found another, maybe little bit more secure and systematic solution. Just complete entries in /etc/fstab and put ignore value in filesystem column. This will prevent partition from mounting and it will not be visible in Nautilus.  (For details see man fstab. :) ) 

Mine looks like this: 
```
# /etc/fstab: static file system information.
#
# <file system>					<mount point>   	<type>  <options>      		<dump>  <pass>
proc           					/proc          		proc    defaults      		0	0
###  partition /dev/sda1 - ex /boot partition
/dev/sda1					/mnt/			ignore	defaults		0	0
### partition /dev/sda2 - windows boot
/dev/sda2					/mnt/			ignore	defaults		0	0
### partition /dev/sda5 - linux swap
UUID=8116a138-6b74-4527-9a8e-d335da6233df 	none       		swap    sw			0       0
### partition /dev/sda8 - windows data
/dev/sda8					/mnt/			ignore	defaults		0	0
### partition /dev/sda9 - free space
/dev/sda9					/mnt/			ignore	defaults		0	0
### partition /dev/sda10 - linux /
UUID=33d0b3f1-9a13-4fdd-8dd3-afceb1f8e2b8	/			ext3    defaults,errors=remount-ro	0	1
### partition /dev/sda11 - linux /home
UUID=3520d0ab-4f65-4385-bab2-99fa7a16636e 	/home			ext3    defaults		0       2
### partition /dev/sda6 - /home/public
/dev/sda6					/home/public		ext3	defaults		0	2
### partition /dev/sda7 - /home/multimedia
/dev/sda7					/home/multimedia	ext3	defaults		0	2
### others
/dev/scd0    					/media/cdrom0   	udf,iso9660 user,noauto		0       0
/dev/sdb					/media/cdrom1   	udf,iso9660 user,noauto		0       0
/dev/fd0					/media/floppy0  	auto    rw,user,noauto		0       0

```

---

