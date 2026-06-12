---
title: "dist upgrade problem?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by lauralee on 2006-06-04
A few days ago I turned my laptop on and my gnome x window wouldn't come up. I don't use my laptop very regularly. The most recent time I used it I added some graphics packages, but beyond that I had so idea what could have caused the problem. My borother suggested that is could be the recent-ish dist-upgrade I did, from breezy to dapper.

Which it could be. So I tried to follow the instructions on 
General 6.06 - HOWTO fix problems regarding broken dependencies
And all went well until
> sudo apt-get install ubuntu-desktop
which didn't work. So I (probably stupidly) went on and did an
> sudo apt-get dist-upgrade

And rebooted. Now my laptop is well and truely ill. On the boot up when we get to 
* checking root file system...
I get
Inodes that were part of a corrupt orphan linked list were found.
/: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
.....
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found
root@sid:~#

I am not a ubuntu fundi and I'm not sure what to do next! Could someone please help? Thanks!

---

### Post by rcarring on 2006-06-04
Running fsck is like running scandisk from DOS. The program should check the file system and repair errors.

---

### Post by lauralee on 2006-06-04
Okay, thanks. I ran fsck and now I'm back to my command prompt, without x!

I ran through the instructions on 
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)
again, and when I get to
> sudo apt-get install xserver-xorg x-window-system-core ubuntu-desktop
I get:

Some packages could not be installed. This may mean that you have requested an impossoble situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
ubuntu-desktop : Depends: alacarte but it is not going to be installed 
(and about another, maybe, 50 other things that are "not going to be installed")

What can I do? Is there anyway to "down-grade" to hoary again?? :-?

---

### Post by rcarring on 2006-06-04
Try just:

```

sudo apt-get install xserver-xorg

```

Then when installed

```

startx

```

If this gets you to the desktop, then log out

Then reboot:

```


sudo shutdown -r now


```

and your desktop should load.

---

### Post by lauralee on 2006-06-04
Thanks.

I tried that. Startx gave some error messages about x already being there (maybe because I had already installed ubuntu-minimal ubuntu-base and since rebooted?) so I rebooted to see if it would work. Now I get about a page of "Segmentation fault"
Then:
---
ALERT! /dev/hda2 does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh" can't access tty; job control turned off
#
---

Oh dear! What is going on?

---

### Post by rcarring on 2006-06-04
type in

```

fdisk -l

```

This will list all the partitions it finds.

Running
```

man fdisk

```

will give the manual pages for fdisk.

From your post it looks like your File Allocation Table has gotten corrupted. I am not sure how to refresh the FAT under Linux.

Hope this helps.

---

