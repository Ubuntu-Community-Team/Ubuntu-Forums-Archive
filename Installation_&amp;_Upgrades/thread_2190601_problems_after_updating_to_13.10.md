---
title: "problems after updating to 13.10"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by desberwado on 2013-11-28
Hello, 

I'm hoping someone can help me with this problem.

I've got an ACER AOA 150 that I use for presenting whilst out of the office. I've been using Ubuntu for a while with no problems. Last night the update for 13.10 arrived and so I pressed 'do it' and left the machine to get on with it.

This morning I woke to find it crashed part way through the installation.

On boot up I now get the following screen:

GNU GRUB version 2.00 - ubuntu3

with options for:
Ubuntu
advanced options for ubuntu
Memory test (Memtest86+)
memory test (memtest86+, serial console 115200)

I've tried them all with out success -  they eventually lead to a screen:

filesystem check or mount failed
A maintenance shell will now be started
CONTOL D will terminate......
filesystems. Any further errors.....
root@stuart -AOA150:~#

If I leave it nothing happens.

I understand that the file system may well have been compromised by the incomplete installation.

Everything is backed up so could someone please advise me on what to do to get the system up and running or how can I get the hard drive formatted and  reloaded before the GNU screen loads?

Many thanks in anticipation
Stuart

---

### Post by fantab on 2013-11-28
Since everything is backed up, Re-installing is always a good option. Download 13.10, burn it to a disk and install. At the installation type screen choose 'Something Else' and direct your install to the existing Ubuntu partition.

Post the output of the following from a Ubuntu DVD/USB install disk:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by philinux on 2013-11-28
Try this at the shell prompt. 

sudo dpkg --configure -a

Then

sudo apt-get install -f

Then

sudo apt-get update ; sudo apt-get dist-upgrade

You may need to fsck the / partition

---

### Post by desberwado on 2013-11-28
Many thanks for your replies fantab and philinux, 

at the GNU page I entered 'c' for a command line and entered the sudo commands but got the message - error: can't find command 'sudo'

I've downloaded ubuntu 12.4 and followed the instructions given by the site for burning it to disk.
 
I've changed the boot order also but it the CD isn't booting up.
I'm clearly doing something wrong - any more suggestions would be welcome

Many thanks

---

### Post by desberwado on 2013-11-29
Many thanks to you fantab and philinux for taking the time to offer your support. It is appreciated.
I have reloaded the OS :-)
A newby with a warm feeling

---

