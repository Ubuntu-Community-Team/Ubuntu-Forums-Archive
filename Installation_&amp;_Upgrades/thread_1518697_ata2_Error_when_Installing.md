---
title: "ata2 Error when Installing"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by Thylacine on 2010-06-27
Okay, I'm not quite new to this sort of thing, but I'm not quite an old fart, either. I've been running Linux since my friend got me addicted to it my Freshman year of highschool - and it hasn't failed me yet. But I have a problem. 

I run an older Compaq tower, one that hasn't given me this sort of error before, but I keep on getting an error that reads something about the ata2 failure. It brings up what looks like a terminal screen and lets me type in commands. I don't know if it is the disc-drive (had issues with the other one that was connected in) or what. 

When I go to type exit (mind you, it looks like this:

[SIZE=1](initramfs)[/SIZE] exit
cp: cannot create '/root/var/log/': No such file or directory
mount: mounting /dev on /root/dev failed
mount: mounting /sys on /root/sys failed
mount: mounting /proc on /root/proc failed
Targest filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg. 

And when I go to try "init= bootarg," I get the following error with Ubuntu 9.04:

[SIZE=1]/bin/sh: bootarg: not found[/SIZE]

While on 9.10 I get an error that says something crashed and tried to kill the init. I have no clue what is going on, or what I'm doing wrong. I have a hard drive with Win98 running just fine on it the other day, but now it's driving me bonkers. 

Also, after typing "init= bootarg" into the command line and then typing "exit" it shows the error:

/init: line 258: cannot open /root/dev/console: no such file
[ 1694.392457] Kernel panic - not syncing: Attempted to kill init!

Anyone had this problem or can help?

---

