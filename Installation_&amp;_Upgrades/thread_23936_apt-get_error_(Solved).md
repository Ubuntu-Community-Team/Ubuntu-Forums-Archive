---
title: "apt-get error (Solved)"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by Beebe on 2005-04-04
Hi

I have just tried to use apt-get for the first time and got this error.....

paul@linux-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Any ideas how i can fix this?

Cheers

---

### Post by Xian on 2005-04-04
You need to use the sudo command alongside your apt-get input.
For example:

sudo apt-get update

That gives you root privileges.

---

### Post by Beebe on 2005-04-05
[QUOTE=Xian]You need to use the sudo command alongside your apt-get input.
For example:

sudo apt-get update

That gives you root privileges.[/QUOTE]

Cheers - all working now! :o)

---

### Post by missmoondog on 2005-11-23
searched for this error and here i am. i get the same as original poster, but when i try the $ sudo apt-get update command, i get this, 'restricted' is not known on line 2 in source list /etc/apt/sources.list. i can't do anything with the src list as far as editing it either. i ave the same src list as listed here, [http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672). help!!

thank you

edit:
yay!! i think i fixed it all by myself! loged in as root, edited file, reloaded the repositories, updated. now to turn off logging is as root and checking it out.

edit 2:
double yay!! all is good.

---

### Post by tOpEzz on 2005-12-22
nice.

---

