---
title: "How moving / (Ubuntu 5.04) on a Reiser4 Partition?!"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by Crypto on 2005-07-07
Hi Dudes,

I've build my own Linux-Kernel with Reiser4 Support and it works very well, right now.

Right now I've following partitions ...

/dev/sda1  --  /boot   -- ext3 (grub)
/dev/sda2  --  not mounted  --  reiser4
/dev/sda3  --  /          --  reiserfs
/dev/sda5  --  swap


Ubuntu is currently installed on /dev/sda3 on a Reiser 3.6 partition.

I want to move my installation from /dev/sda3 to /dev/sda2 (  / should become reiser4 )  but have no idea how to solve it.

I tried it with mounting /dev/sda2 and copy the files on it. After that I've modified the grub menu.lst and edited the /dev/sda3 entries to /dev/sda2

After restarting the system I got a error message (dont remember) and the system hungs ...


How to move the installation *safe* on the other reiser4 partiton !?

Thanks ... (and sorry for the language) :)

---

### Post by Crypto on 2005-07-07
I've boot my system via a reiser4-ready live-cd (kanotix) ....

I've tried it with copy the files (cp -a * ...) from the one to the other partition, edited the fstab and mtab files ... and de grub menu.lst ...

Now I'm getting following error after rebooting:
> 
cramfs: wrong magic
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!  ](*,)

---

### Post by geearf on 2005-07-07
i've done it with a gentoo live CD, and a stage4 back up (make a .tar of the partition i want to save) a bit long, but it worked :)

---

### Post by geearf on 2005-07-07
oh, another thing, i don't know how the system will do if you change its primary partition number, it may not like it in fact :(

Have you changed it in fstab ?

---

### Post by Crypto on 2005-07-07
[QUOTE=geearf]oh, another thing, i don't know how the system will do if you change its primary partition number, it may not like it in fact :(

Have you changed it in fstab ?[/QUOTE]


I've also tried it with installing it on sda2, making a backup (with copy -a ) on sda3 and format sda2 with reiser4 - and restore it .... no chance :(

I've edited fstab, mtab & menu.lst (and build myself a grub loader 0.96 with reiser4 support ... didn't help.

Right now I'm compile the kernel again but with build-in reiser4 support (and not as module)

---

### Post by Crypto on 2005-07-07
Build-In Reiser4 Support in Kernel works ... - Module makes trouble :)

---

### Post by geearf on 2005-07-07
i've always done it with built in.

I think you need initrd if you want it as a module.

---

### Post by mingus on 2005-07-07
This worked for me, although with Reiserfs.  The syntax I used was:

#mkdir /newsystem
#mount <device/partition> /newsystem
#cd /
#cp -axv . /newsystem

the new partition needs to be formatted first

the "x" instructs copy to stay on the filesystem

---

### Post by geearf on 2006-02-10
I don't know why, but I cannot make my / a reiser4 anymore, no problem with my /home, but it never works with /.
If anyone knows what I am forgetting please lend me a hand, cause I know it used to work before, but not anymore ... don't know why :(
I had reiser4 as built it, I may try later as a module, you never know ..

---

### Post by geearf on 2006-02-11
No idea up there ? :(

---

