---
title: "I f'ed up GRUB...."
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by MicroChris on 2005-03-22
Hey guys,

I messed up grub by trying to add my own splash image.. I guess the image doesnt want to load, so the menu doesnt load either.. It boots right into XP.

I tried the whole "boot from CD and do this and that" but none of it worked.. 

Help...please :D

Thanks guys,
Chris

---

### Post by bored2k on 2005-03-22
[QUOTE=MicroChris]Hey guys,

I messed up grub by trying to add my own splash image.. I guess the image doesnt want to load, so the menu doesnt load either.. It boots right into XP.

I tried the whole "boot from CD and do this and that" but none of it worked.. 

Help...please :D

Thanks guys,
Chris[/QUOTE]
 If you did the "whatever cd thing" it should work so its not us the faulty ones. Be f' explicit. 

And off record: if you aren't sure what you're doing, do not f' with Grub, it does not like to be bothered. And for the record: next time, install grubconf and do things the gui and safe way .

---

### Post by MicroChris on 2005-03-22
You're right. 

It just totally slipped my mind that the splash wouldn't work. Didnt think it was something that would totally crash grub.

Ok, I boot to the CD and do 

```
mkdir /mnt/temp
``` 

so I can do 

```
mount /dev/hda1 /mnt/temp
vi /mnt/temp/boot/grub/menu.lst
``` 

but I cant even get passed the mkdir part, cause I get an error (cannot create, blah blah)

Thanks,
Chris

---

### Post by bored2k on 2005-03-22
fdisk -l /dev/discs/disc0/disc

Are you certain the disk you want to mount is in /dev/hda1 ?

---

### Post by MicroChris on 2005-03-22
yep

---

### Post by bored2k on 2005-03-22
[QUOTE=MicroChris]yep[/QUOTE]
 bummer .

Try creating a dir on / , not mnt
for example:
mount /dev/hda1 /please_work

---

### Post by MicroChris on 2005-03-22
I get:

```
mount: /dev/hda1 is not in /etc/fstab
```

I tried /dev/hda, /dev/hda 1 2 3 4, heh. nothin

Thanks for trying to help me through this though, I appreciate it.

-Chris

---

### Post by MicroChris on 2005-03-22
I'm booting to the CD, waiting for it to go to partitioner, then Ctrl+Alt+F2, then enter.

Is this the right way?

I just did "mount /dev/hda1 /please_work" and it didnt work.

---

### Post by bored2k on 2005-03-23
[QUOTE=MicroChris]I'm booting to the CD, waiting for it to go to partitioner, then Ctrl+Alt+F2, then enter.

Is this the right way?

I just did "mount /dev/hda1 /please_work" and it didnt work.[/QUOTE]
 Yeah .

If you hit cat /etc/fstab it will show somethng like: 
>  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


But that is really weird as I did that trick last week and I mounted with no problems .

Ill tell you this though: If you get a live disc you will probably be able to write on top of it [a small one like damn small linux should suffice] .

---

### Post by MicroChris on 2005-03-23
Thanks again bored2k!

I had to get the DSL disk, and do everything there, but it worked.

To anyone having the same problem as me, make sure you delete the /.menu.lst.swp file that the cd will create.. If you dont remove it, it will still boot the old, non-working menu.lst.. Weird.

Anyway, thanks again bored2k!

-Chris

---

