---
title: "Latest 10.04 update went crazy--I'm in over my head!"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Seamless in Northampton on 2010-10-28
The latest upgrade to my 10.04 system has done--well, something. I get past the Grub menu, then the screen goes blank. Then the screen goes dead, as in not just blank.

The recovery version of the latest kernel seems like a very long recitation of errors. I just want to get the machine to boot, then I want to retrieve my data and start with a fresh install.

I can type out more of what I see if it will help, but the end of what I'm currently getting reads this way --***=numbers I didn't want to type because they seem long and irrelevant :) --

udevd[311]: can not read '/etc/udev/rules.d/z80_user.rules'

fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda1
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/
/dev/sda3: clean, ***/*** files, ***/*** blocks
/dev/sda4: recovering journal
/dev/sda4: clean, ***/*** files, ***/*** 
init: ureadahead-other main process (856) terminated with status 4
init: ureadahead-other main process (866) terminated with status 4
init: ureadahead-other main process (869) terminated with status 4
[***] FAT; bogus number of reserved sectors
mount: wrong fs type, bad option, bad superblock on /dev/sdb3, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg I tail or so

mountall: mount /media/sdb3 [870] terminated with status 32
init: ureadahead-other main process (875) terminated with status 4
init: ureadahead-other main process (878 ) terminated with status 4
init: ureadahead-other main process (881) terminated with status 4

I can't see what's above that, but it looks like more of the same.


I'm over my head entirely. I'm several years into Ubuntu,but I'm not the world's best at the nuts and bolts of the system, though I've solved a few tough issues with the help of the forum. Any advice would be most appreciated--I am a musician, and I was in the middle of a big audio project when this happened. I can get to the data, but I need to finish the project!

Thanks in advance.

---

### Post by ronparent on 2010-10-28
The recovery mode for the latest previous kernel will probably be listed in the grub menu (if that hasn't been yet fowled). Try booting to that and selecting the dpkg item (if there). If not the root terminal. In that case try typing 'sudo apt-get upgrade'. With luck your upgrade may pick up where it left off. I resorted to the dpkg item yesterday and recovered from an interrupted upgrade and ended up with, in my case, a working 10.10 installation.

---

### Post by Seamless in Northampton on 2010-11-07
Well, many days in, I'm ready to bang my head against the wall. 

I have:

1) tried the sudo apt-get upgrade method, both from a command prompt when trying and failing to boot from an earlier kernel, and from terminal using the Live CD. It tells me it can't resolve host Ubuntu, and fails to retrieve any packages.

2) checked that the host 127.0.0.1 (if I remember correctly) is listed in the appropriate place. It is.

3) Tried to edit my fstab to ignore the problem partition. I don't have permission to save the file, and I can't seem to give myself the proper permission, despite mounting the drive with -rw. 

4) Given up all that and decided to do a fresh install of Ubuntu on another partition so that I can then access my old files and start over. Install aborts due to an input/output error. New CD didn't help.

What the heck do I do now? Can I install a new instance of Ubuntu using Wubi and accomplish the same thing I would in 4?--Windows does work. I am extraordinarily frustrated. Any tips appreciated.

---

### Post by P4man on 2010-11-07
Boot from a livecd, and backup anything you havent backed up yet (assuming you can still mount your partitions).

Next, check your drive for problems. In system > administration > disk utility check the smart status of your hdd. I suspect your drive is dead or dying.

edit: this is a wubi install? Dont do that. But anyway, if there is an NTFS problem, it would affect ubuntu too. Run chkdsk /F

---

### Post by Seamless in Northampton on 2010-11-07
Thank you--I'll give that a try right away. And no, this is not a Wubi install.

---

