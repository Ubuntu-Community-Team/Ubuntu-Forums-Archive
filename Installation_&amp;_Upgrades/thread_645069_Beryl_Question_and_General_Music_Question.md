---
title: "Beryl Question and General Music Question"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by NobleRooster on 2007-12-19
I got my Graphics card installed and Beryl running,  But is there anyway that Beryl can be setup to start on startup?  I can't seem to find an option or anything so if anybody knows how to do this help is appreciated.

Also, I'm having trouble with music.  I am dual booting Windows Vista and Ubuntu 7.10.  Well, my Ubuntu partition is pretty small and I don't want to take up my already small Ubuntu partition with all my music.  So, I just tell me music player to grab the music from the other partition.  But every time I close out the music player or restart/logout...it says that it can't find the files. Anybody know how to fix this problem?

---

### Post by Pumalite on 2007-12-19
1.-Beryl is compiz-fusion now a days
2.-Post:
sudo fdisk -lu

---

### Post by NobleRooster on 2007-12-19
> **Pumalite said:**
> 1.-Beryl is compiz-fusion now a days
2.-Post:
sudo fdisk -lu
Sorry, didn't know it was that now-a-days, it's just called Beryl on here so that's what I put it as.

As for the partitions:
[IMG]http://i81.photobucket.com/albums/j229/JBennett89/thing-2.png[/IMG]

---

### Post by Pumalite on 2007-12-19
So, in which partition is your music?
Also, in your system compiz-fusion should come installed by default. You just have to have the right card, the right driver and enable it.

---

### Post by NobleRooster on 2007-12-19
I'm pretty sure it's the one that has the first asterick/star in front of it.
/dev/sda3

---

### Post by Pumalite on 2007-12-19
Go to Places>Home and look on the left. See if it is there and you can mount it with a double click.

---

### Post by NobleRooster on 2007-12-19
I double clikc "OS" which is the partition that the music is one, and it creates a link on my desktop.  I added the music to my media players, but wen I restart, it all goes away.

---

### Post by Pumalite on 2007-12-19
Post:
cat /etc/fstab

---

### Post by NobleRooster on 2007-12-19
I didn't screen shot this time, too much trouble.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c2962ec4-c866-482e-bd5b-16a489847b80 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=8be6f37f-a392-4c55-868f-339c7033c7b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


---

### Post by Pumalite on 2007-12-20
Backup first
sudo cp /etc/fstab /etc/fstab.back
gksudo gedit /etc/fstab
add this line at the end:
/dev/sda3 /media/disk udf,iso9660 user,noauto,exec 0 0
Save and exit.
Go to Terminal:
sudo mkdir /media/disk(Enter)
Reboot
Post:
mount

---

