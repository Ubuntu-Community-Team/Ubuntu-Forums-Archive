---
title: "Just upgraded to lucid and now /dev/md0 is gone away, no boot"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by peufeu on 2010-06-06
Well, here I am with a rather annoying problem... if some of you guys can provide any help I'd be very grateful.

I had a perfectly working 9.10 Kubuntu configuration which I updated to 10.04 and now the thing won't boot at all.

The machine is a Core 2 Quad and has 5 HDDs. OS is 64 bits.

/boot isn't RAIDed, it's a plain ext3 on sda1.
/ is on a RAID which is /dev/md0 made of sda3 and sdb3

The other 3 disks make up a 2TB RAID5 but they're not part of the problem...

I used the kubuntu update wizard to update and all went well, except phpmyadmin which didn't update, but that's probably not what's causing this.

After the update, I boot, and :

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6417.jpg[/IMG]

So, Grub is happy. I wonder why it didn't install a new kernel version, this is still my old one, but hey, it worked.

The Kernel shows its usual display of stuff, so it's loading correctly, thus Grub is OK.

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6411.jpg[/IMG]

But :

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6412.jpg[/IMG]

I've seen this before, so I apply the usual fix : madam, assemble the array.

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6413.jpg[/IMG]

It looks like the md0 is working. Note there is a strange display bug, it display "as3emble" instead of "assemble"... but I typed "assemble" and it works... this is bizarre...

So since md0 is up I exit the busybox and ...

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6414.jpg[/IMG]

..fail.

/dev/md0 does exist though

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6415.jpg[/IMG]

then it gets weirder : it's there, but it's not there.

[IMG]http://peufeu.free.fr/lucid-crash/IMG_6416.jpg[/IMG]

I've been using linux for about 10 years but never saw this one !

Got any idea guys ?

---

### Post by peufeu on 2010-06-06
What I usually do is :

- degrade the md0 RAID1, removing 1 drive
- zap the drive and create a new RAID, say md2, with 1 drive
- make a clean reinstall on md2
- boot it
- copy all the old data from the old md0 to the new md2
- zap md0, add it to md2, and sync, thus getting a RAID1 again

However in this case I got a non-dumped Postgres database that I would like to recover, and for this I need the same version of Postgres that I had.

This time I was stupid and did not backup, shame on me. So I just need this system to boot once to back up everything and then zap it and reinstall.

Gonna try with the LiveCD...

---

### Post by peufeu on 2010-06-06
Using the 9.04 LiveCD which has the same version of Postgres and MySQL that I had installed, I was able to dump all databases safely. So, after the backups are done, this system is getting zapped, unless someone comes up with an idea to un-screw this install.

This is what I love about Linux : even when it commits suicide, you're not 100% screwed.

---

### Post by ft_mn on 2010-06-06
Hi, i ve just updated to ubuntu 10.04 the thing is that i cannot boot my Windows Xp even if I can see the label  win xp (whatever) loader  on my GRUB screen... i can boot ubuntu normally but when im about to boot XP the computer reboots automatically. My PC is a self-made (no brand like HP or DELL) desktop ... any ideas to fix this plz?

---

