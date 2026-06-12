---
title: "dapper rc doesn't automount ntfs partition"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by x3non on 2006-05-31
Hi all,


I put a fresh install of dapper RC on my notebook, but dapper doesn't automount NTFS partitions (and it doesn't put the shiny icon on the desktop) as it used to do since flight 5.

Anyone knows why/and how to fix it?

Other than this everyting works flawlessy...simply wonderful :D

Many Thanks,

X.

---

### Post by Rackerz on 2006-05-31
[QUOTE=x3non]Hi all,


I put a fresh install of dapper RC on my notebook, but dapper doesn't automount NTFS partitions (and it doesn't put the shiny icon on the desktop) as it used to do since flight 5.

Anyone knows why/and how to fix it?

Other than this everyting works flawlessy...simply wonderful :D

Many Thanks,

X.[/QUOTE]

That's rather strange, Dapper automounts both my NTFS drives. Does it show your drives in the computer menu?

---

### Post by x3non on 2006-05-31
[QUOTE=Rackerz]That's rather strange, Dapper automounts both my NTFS drives. Does it show your drives in the computer menu?[/QUOTE]


nope, i have to manually mount them...

---

### Post by Rackerz on 2006-05-31
/dev/hda1 /media/hda1 ntfs umask=0222 0 0
/dev/hdd1 /media/hdd1 ntfs umask=0222 0 0

That was my fstab from Breezy after I added it to automount my Windows drives. Add that to your fstab. Make sure you change the driver information though, because yours are probably named diffrent. You may also have to restart after editting your fstab.

---

### Post by x3non on 2006-05-31
[QUOTE=Rackerz]/dev/hda1 /media/hda1 ntfs umask=0222 0 0
/dev/hdd1 /media/hdd1 ntfs umask=0222 0 0

That was my fstab from Breezy after I added it to automount my Windows drives. Add that to your fstab. Make sure you change the driver information though, because yours are probably named diffrent. You may also have to restart after editting your fstab.[/QUOTE]

thanks for your help Rackerz, I know how to edit fstab, I'm just wondering why it isn't automatic no more! ;)

---

### Post by Rackerz on 2006-05-31
Yeah me too. It's strange because mine automount. Did you install from the livecd by anychance?

---

### Post by x3non on 2006-05-31
[QUOTE=Rackerz]Yeah me too. It's strange because mine automount. Did you install from the livecd by anychance?[/QUOTE]

yep I did a fresh install this morning with Dapper RC liveCD.

After that I obviously did an "apt-get update && apt-get upgrade" ;)

---

### Post by Rackerz on 2006-05-31
I did the same thing, how strange.

---

### Post by peter_nz on 2006-08-21
Hi I have same problem but I installed dapper on two laptops one of them shows the ntfs partition and icon on desktop perfect

the other one I cant access the ntfs partition 

The ony difference I can think of is that I choose manual partitioning on the perfect instalation 

and auto default resizing on the other laptop maybe something to do with it ?

---

### Post by peter_nz on 2006-08-25
ok I got it fixed can access windows partition in both laptops perfectly now . by editing fstab So first things first create a directory to mount your windows partition on    open a terminal              
code =   sudo mkdir /mnt/media/hda1

then also in the terminal enter this

 sudo gdeit /etc/fstab

You will see a text file that looks alot like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

T/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   1 
 the line that is really important for windows   
partition is this one

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

odds are that line is missing or different in your install.
the space between the 6 fields is important so copy and paste probably best option here.
then click on save then exit gedit and reboot computer ,cross your fingers and your icon for windows partition sould be there waiting for you on your desktop. :grin:  good luck and may the spirit of UBUNTU b.e with you

---

