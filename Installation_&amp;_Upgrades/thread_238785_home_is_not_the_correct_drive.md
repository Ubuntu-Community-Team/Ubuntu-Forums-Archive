---
title: "/home is not the correct drive??"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2006-08-18
Hi guys..

I have a fresh install of ubuntu on my laptop.
I put /home on its own partition. But When I go to the home folder it takes me to a "home" folder located in the /root.
I tried to make "sda8" the /home location but it tells me /home/rush isnt located there. So ai moved that file to the new location but still no luck?
Can anyone help please..

---

### Post by givré on 2006-08-18
Let see your /etc/fstab

---

### Post by floyd27 on 2006-08-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda8       /media/sda8     ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

###################################################################3

I tried to change /media/sd8 to /home but thats where the problems start.
After doing sudo mount -a I can no longer use konqueror and most other things until I change it back.
I also copied the /home/rush folder to the "sda home" but that didnt help..

---

### Post by floyd27 on 2006-08-18
I have tried all day to fix this but no luck..
So is it a fresh format again..

It just doesnt seem like I should have to just to move the /home folder to a different partition?

---

### Post by avtolle on 2006-08-18
[http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html) should be helpful if you haven't already reformatted.

---

### Post by givré on 2006-08-18
Sorry dude, i was away :cool: 
so if i understand well, you want to your /dev/sda8 partition to be your /home partition. So on that partition, it must contain only:
- the directories of the user
- the directory lost+found.
So if you are the only user, /dev/sda8 must contain at it base, 
rush/ & lost+found/
Is that what you have done?
Also the rush directory must contain all your config files (or it will probably fail to start). Do you have still them.

---

### Post by floyd27 on 2006-08-18
Yes that is what I am trying to do..

I still have all the config files and actually tried to just move the folder into the new /home but it didnt work..?
I will try with just the folders you listed and get back to you.
thanx for the help..

---

