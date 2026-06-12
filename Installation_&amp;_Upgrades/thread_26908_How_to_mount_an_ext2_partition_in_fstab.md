---
title: "How to mount an ext2 partition in fstab?"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by [censored] on 2005-04-14
ello. I have an ext2 partition with lots of stuff on it. I can mount it from the command line using mount, but how do I set it up to mount in fstab?

I tried adapting the instructions here 
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
and
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat) 

so that the last line in fstab looks like this: 
/dev/hdb2       /mnt/storage    ext2 umask=000       0       0

but it doesn't seem to work.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE='[censored]']ello. I have an ext2 partition with lots of stuff on it. I can mount it from the command line using mount, but how do I set it up to mount in fstab?[/QUOTE]

Try replacing "umask=000" with "defaults". Why are you setting the umask to 000 for that filesystem, anyway?

---

### Post by [censored] on 2005-04-14
wicked thanx.

I had it at unmast=000 because quite honestly I have no idea what that part of the syntax means.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE='[censored]']wicked thanx.

I had it at unmast=000 because quite honestly I have no idea what that part of the syntax means.[/QUOTE]

Don't feel bad; I don't fully understand umask myself, so I just leave it the hell alone. :)

---

