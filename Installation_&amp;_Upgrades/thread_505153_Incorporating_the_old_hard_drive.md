---
title: "Incorporating the old hard drive"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Thrasyllus on 2007-07-19
Hi! I have just installed Feisty on my master drive, hda. When I started the procedure I specified only that drive because the other disk (which used to be the master but is now the slave) contained two old partitions - one for DR-DOS and one for Fedora 2 (hdb3). You will gather from this that I seriously procrastinate about upgrading: the reason is that I have witnessed some destructive installations in the past, hence my reluctance. I wanted to protect my old data, some of which is not backed up. Ubuntu was delightful to install, however.

Here's my problem. Ubuntu's great multiple boot lets me go to either Feisty on hda or Fedora on hdb, and I go to DR-DOS with a system floppy. But none of these systems can see any of the others. I would like to incorporate the old personal ~ filesystems on the slave drive into the the Feisty home directory (or another directory, I'm not fussy), destroy the system stuff on hdb3 I no longer need, and forget Fedora.

I would also like to be able to write text files from linux to DR-DOS and read DR-DOS files while in linux.. This used to be possible with Fedora but when I swapped hard disks that capability was broken.

So: (1) what is the procedure for incorporating hdb into an already-installed Feisty? (2) Will there be a problem when Feisty encounters two roots on two different drives? If so, how to deal with it? (3) How to get Feisty to read DR-DOS files and copy to the DR-DOS partition?

Uh, what else...? I gave myself a different user name on Feisty from the one I used to have on Fedora - in case that helps.

Thanks in advance. I have *many* more questions...

---

### Post by aquavitae on 2007-07-20
You simply have to mount the other partitions.  There is a tool under system settings to do this, but I'l a bit of a command line person so I've never used it.  On the command line (i.e. in a terminal), the command to mount a file system is:```
sudo mount /dev/hdb3 /mnt/fedora
```Replace /dev/hdb3 with whatever the device name is you want to mount, and /mnt/fedora with a path to mount it on.  /mnt/fedora must be a valid path, i.e. you might have to use 'sudo mkdir /mnt/fedora' to create it.

In order to automatically mount ever time you start up, edit the file /etc/fstab (as root) and add the following line for each filesystem (replacing /dev/hd** and /mnt/*** with the correct values):
```
/dev/hd**  /mnt/****  auto  defaults,rw,users 0 0
```
I'm not at my linux computer atm so I cn't check that - I might have got the order wrong, but it should be obvious from the other lines in fstab if I have.  You could replace the word 'auto' with the file system type (e.g. ext3, reiserfs, etc), but auto should work fine.  Once you've added the lines, save and close, and in a terminal type the command ```
sudo mount -av
```You should now be able to read the partitions from the mount location (i.e. /mnt/fedora, etc).

---

### Post by Thrasyllus on 2007-07-20
Thank you aquavitae! Just the info I was looking for. I'm a command line guy too - a refugee from the old eight-bit world.

---

