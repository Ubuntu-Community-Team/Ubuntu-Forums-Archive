---
title: "Upgrading, with the option to downgrade"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2014-04-21
I would like to upgrade an Ubuntu 12.04 LTS machine to 14.04 LTS. However, since I don't know how well 14.04 is going to work (driver compatabilities, etc), I want to do it in such a way that I would have the option to downgrade if I wanted so.

The OS is installed in an ecnrypted hard drive. I want to know if there is an easy way to take an image of the existing partition, so I can restore it in case of downgrade. My past experience with backing up and restoring partitions never involved using an encrypted system.

Any advice is highly appreicated.

---

### Post by PaulBx on 2014-04-21
You already have that option, it's called backup (although the software updater really ought to suggest that to people in my opinion, before proceeding).

Before making any major changes to my system, I boot a Puppy Linux CD (just my personal preference, because I am used to it - I'm sure there is a Ubuntu-flavored way of doing it). In that case, my system disk is not mounted, which is important. Then I plug in a backup USB drive, mount that, and then in a console window use dd (along with compression) to image my system disk to a file on the backup drive. The particular command I use is

```
dd if=/dev/sda bs=1024 conv=noerror,sync | gzip -c -9 > /mnt/sdc1/LenovoG780/backup-sda-1.gz
```

If I need to restore from that file I do this:

```
gunzip -c -9 /mnt/sdc1/LenovoG780/backup-sda-1.gz | dd of=/dev/sda
```

Of course this assumes sda is the system disk and sdc1 is the backup drive. It will take a long time if your system disk is very large. Mine is an SSD so it is reasonable. Be careful with these commands; dd can cause havoc if not run properly.

---

### Post by 23dornot23d on 2014-04-21
Out of interest only .........

What is your layout on the drive at the moment ............

Can you run gparted and give a screen shot here ............

When there is plenty of room on a hard drive ....... install alongside can be a very good way - with a separate /home partition

or (separate data partition / partitions ...)

I run many versions of linux and many OS's from either USB hard drives or from the internal drive ........

I often see these types of questions and wonder if people realise that we are not stuck to just one or 2 OS's on a drive.

The thing with many choices ........ is you can upgrade or add new .......... and if your data is in separate partitions - you
can go to it ........ ( only real problem then comes down to what programs you need to install ...... which becomes a routine after a while )

Even for that - there are ways with scripts .......... or something I use is Timeshift nowadays ...... its like a restore program to an earlier snapshot.

It can even act like a clone ...... to add it to a USB drive or somewhere else .......... needs a little bit of reading up on and understanding.

But works for me ............ just thought I would say ........ but I have never used encrypted - so that is the part I cannot help with.

[http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html](http://www.ubuntugeek.com/timeshift-provides-system-restore-functionality-in-ubuntu.html)

If say your install is 30 gig .......  ( then 70 gig is needed .... for a backup and restore to the same drive ) .......... but only 40 gig or more to
a external drive to be safe as sometimes it under-calculates the room it needs. ..........

The times I have used it - its saved me lots of hassle and also is quick to restore ... faster than a install ........ so now I have 3 versions of
my favorite OS on different drives and can mess with some as test OS's ..... knowing that my original is safe.

Try things out on the Test ones ........... then when sure I know any problems - go and do the proper install or changes on my original.

Leads to me having one really good system ..... as well as having backups that run on external hard drives as well ..........

Depends if you like having copies of things and backups ....... but it works well for me.

---

### Post by hojjat on 2014-04-22
This is how my partitions look like. I think I am going to create a backup partition and copy stuff using dd. That is assuming that I can figure out how to mount my encrypted volume :)

[ATTACH=CONFIG]252375[/ATTACH]

Also, because it is an ecrypted system, gparted cannot create/edit paritions that are inside /dev/sda2

---

### Post by Mark Phelps on 2014-04-22
>  I want to do it in such a way that I would have the option to downgrade if I wanted so.

Sorry, but there is no "downgrade option" when installing or upgrading Ubuntu.  Of course, you could do an image backup and then restore over the new version -- but that's not really a "downgrade option".

---

