---
title: "Troubles installing Quake 2"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by Virtuous on 2007-02-14
I'm having troubles installing Quake 2. I made a directory and I have the cd. but when I go into terminal to install the files I get this error:

root@xenon:/usr/local/games/quake2# cp -r /mnt/cdrom/Install/Data/*
cp: missing destination file operand after `/mnt/cdrom/Install/Data/*'

What do I do to correct this? Thanks. :(

---

### Post by halfvolle melk on 2007-02-14
Look at the error message:
```
cp: **missing destination** file operand after `/mnt/cdrom/Install/Data/*'
```
cp works like this:
```
cp /source /destination
```
In your case it might look like this:
```
cp -r /mnt/cdrom/Install/Data/ /home/virtuous/quake2
```
You won't need the * because of the -r (<- recursive). Look at man cp for more info on how the command works.

---

### Post by Virtuous on 2007-02-14
I think one of the major problems for the installation not happening is that. I'm not able to mount the Quake2 cd. It's in my cdrom drive and my ubuntu reads it. I typed in the command to mount it.

mount -t iso9660 /dev/cdrom /mnt/cdrom
mount: mount point /mnt/cdrom does not exist

I've been following steps with Linux Quake HOWTO: Quake2

[http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html](http://www.linuxdocs.org/HOWTOs/Quake-HOWTO-3.html)

Now my question is how do I find my cdrom mount point? :(

---

### Post by halfvolle melk on 2007-02-15
You can make it
```
mkdir /mnt/cdrom
```

---

