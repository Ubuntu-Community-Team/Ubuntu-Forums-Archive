---
title: "Installs but can not boot. (soft raid)"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by OkydOky on 2006-06-30
Hello,

I am trying to configure software raid on two Identical Hard drives of mine..
I would have used the Bios raid, but unfortunatelly it seems there is no support for Uli Bios raid.

So I tried doing software Raid.
I, used the Text installer..

I partitioned both Drives life so:

50 MB
1.5 MB
118.5 MB

All configuered as Raid partitions

The configured Software raid:
Raid 1: 50MB   /boot
Raid 0: 3 GB   swap
Raid 0: 237 GB   /

The install went fine
Grub installed on Md0 the raid 1 partition.

Then when I boot, Grub leads fine but I get this when it tried to mount the root file system:


```
Uncompressing linux... Ok, booting the kernel.
mdadm: /dev/md0 has been started with 2 drives.
mdadm: /dev/md1 has been started with 2 drives.
mdadm: /dev/md2 has been started with 2 drives.
mount: Mounting /dev/md2 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list if built-in commands.

/bin/sh: can't access tty; job control turned off
#_

```


I am still rather new at linux... thsi is my 1st raid attempt with it, and of course I can not get it working ;)

I find it odd that the installer went fine, but I then get this.
Do I need to change sometyhing in GRUB? or.. it this something completelly different?


EDIT:

I now tried a Suse 10.1 install, and everything worked fine. Is there a fix for above and ubuntu?

---

### Post by OkydOky on 2006-07-03
No reply? :(

---

### Post by jsimmons on 2006-07-03
[QUOTE=OkydOky]No reply? :([/QUOTE]

Get used to it. Nobody is replying to these kinds of posts other than to say "me too."

---

### Post by houstonbofh on 2006-07-03
[QUOTE=jsimmons]Get used to it. Nobody is replying to these kinds of posts other than to say "me too."[/QUOTE]
Not true.  I have responded to a few posts like this (just not software raid) today.  I didn't on the weekend... :rolleyes:  The problem is that not many people are running software raid, so you have a limited pool of people who can help you.  Be patient, and bump occasionally.  That and continue searching.  You may find a solution first, and if you do, don't forget to post it!

---

### Post by go2dell on 2006-07-05
First, congratulations on deciding to use RAID, but be absolutely certain you keep excellent backups.  Although I've had very few problems with RAID under Linux, when it gets flakey, it gets very flakey!

Since this appears to be a new install, I'm guessing you're not particularly set on the partitions you configured, so I have a few suggestions that may make life easier for you.

First, don't put your swap partitions on soft RAID (or even on hardware RAID unless you have a good reason for it).  Linux is smart enough to do the disk striping thing for you, eliminating some of the soft RAID performance hit when you start swapping.  Just get rid of the RAID 0 partitions you're using for swap and make them standard Linux Swap partitions (type 82).  Then edit /etc/fstab and make sure you have entries for both swap partitions.  You will probably be able to simply copy the entry the installer builds for you, which will only be for a single swap partition.  In the options for each swap entry (the "sw" or "defaults" entry) add "pri=-1".  It should look something like this:
```
/dev/hda2   none   swap   sw,pri=-1   0   0
/dev/hdb2   none   swap   sw,pri=-1   0   0
```

I have previously run a /boot partition on RAID 1, but I haven't tried it on Ubuntu precisely because the installer doesn't seem to handle multiple RAID partitions very well.  Existing partitions it can set up without much trouble.  You will probably need to manually create your RAID 1 partitions, using mdadm, before beginning the installation.  While you're at it, do the RAID 0 as well, so all that's left for the installer is for you to choose the mount points.

If that fails, you may want to just forget about running /boot on RAID anyway, since it's easily the least important part of your particular setup.  Any failure that would cause you to need the second RAID 1 partition will possibly be a disk failure anyway, and your RAID 0 partitions will both be unrecoverable if you have a dead drive (100% data loss).  You'll have bigger things to worry about than recovering your kernel, since not even booting from a CD will let you recover your data.  :rolleyes: 

Backup, backup, backup!

---

