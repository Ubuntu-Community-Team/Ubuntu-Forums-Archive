---
title: "disk partitioning layout in Breezy"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by django_xl on 2005-11-05
Hi folkos,
this is how I currently installed Breezy (output of a df -h):

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             714M  655M   21M  98% /
tmpfs                 500M     0  500M   0% /dev/shm
tmpfs                 500M   14M  487M   3% /lib/modules/2.6.12-9-amd64-generic/volatile
/dev/sda5              45M   12M   30M  29% /boot
/dev/sda6             2,8G   65M  2,6G   3% /tmp
/dev/sda8              44G  1,8G   40G   5% /usr
/dev/sda7             4,6G  516M  3,9G  12% /var
/dev/sdb2             3,8G  711M  3,1G  19% /media/ipod

The reason I did it like this is that I expected Ubuntu to install every package in /usr.....but now I see I'm running out of disk space (used to the freeBSD way).

The / partition is used when I install packages and I'm running out of diskspace already.

What can I do to solve this? Or do I have to totally reinstall Breezy?

---

### Post by samdude9 on 2005-11-05
i think you have to specify a different folder though the kernel...

---

### Post by spizkapa on 2005-11-05
[QUOTE=django_xl]Hi folkos,
this is how I currently installed Breezy (output of a df -h):

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             714M  655M   21M  98% /

The / partition is used when I install packages and I'm running out of diskspace already.[/QUOTE]

The / partition is NOT used when you install packages. You have made / only 714MB which is a little small. You also do not have a /home partition so anything in your home directory and any other user's home will be under / this way. You only have 21M left on / so yes, you've got a problem coming up.

I would say that the best way forward is to reinstall, not because it's impossible to fix the situation but it will be more hassle than it's worth. You can unmount the root partition and you can change the root partition with the system running but it's easy to get confused. Bottom line: back up, reformat, choose a different partition scheme and reinstall.

If you're not very experienced with Linux, I would let ubuntu do its thing with partitioning, it's actually pretty good. If you still want your own partitions, mak one for /home, one for swap (twice the size of your ram, normally) and the rest as /. It's simple and you'll be up and running quickly.

For your information, the partitions only help you recover your system after a hard drive failure since the failure is contained, theoretically, within the partition that fails. This is true for multi-disk installations but you only have one hard drive so just go for the east choice. The only other benefit comes from being able to reinstall the OS and keep your data intact but these days, there are CD/DVD burners to help you with that.

Good luck.

---

