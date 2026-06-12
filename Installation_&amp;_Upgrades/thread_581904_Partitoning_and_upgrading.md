---
title: "Partitoning and upgrading"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Calash on 2007-10-19
I ran the upgrade to Gutsy last night, but I have so many tweaks that it is not working very well (Gnome is not launching at all).

So, I was thinking this is the perfect opportunity to reload my system and partition it just the way I want.

Currently it has a 250gb drive divided into several parts

Ubuntu - 3gb swap, 180gb /
XP Application - 10gb
XP Game - 60gb


What I want to do is dump the application partition, separate /home into it's own partition, and reformat the game partition, leaving it at 60.

My question is how large should a home partition be?  Does it need to be more than the / partition or should the be closer in size?


Here is what I am thinking, but is it a good setup..

Ubuntu -
/ - 100gb
/home 90gb
swap 3gb

XP Game - 60gb

---

### Post by logos34 on 2007-10-19
If you make a separate /home partition, then ~10 GB should be plenty for /.  3 GB for /swap is a waste IMO; 1 GB should be enough for average use, 2 GB if you'll be doing video editing or other memory-hungry tasks.  The remainder for home.

See this illustrated guide to creating partitions and mount points during install:

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-10.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-10.html)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)

---

### Post by Calash on 2007-10-19
I noticed that most guides say 1-1.5x your current system memory for swap.  I have 3gb, so that is why I had that set, but if it is too much I can alwayse change that.

I ended up getting my current install working (Turned out it was issues with Compiz fusion from an external Repo, removed it and reinstalled from standard repos and it is solid now).  I still may adjust the partitions, having /home on a seporate area seems like a wise thing to do.

Thanks for the feedback and links :)

---

### Post by dabl on 2007-10-19
> **Calash said:**
> 

I noticed that most guides say 1-1.5x your current system memory for swap.



That is true, but it seems to be rather obsolete guidance, except for the case where you have a laptop and you want to use the "hibernate" function.  If you have a desktop. or you're not going to use "hibernate", I"m hard-pressed to imagine why you would need more than 0.5 GB of swap.  I've been watching mine for a year, and it's never used more than about 200MB of swap, no matter how hard I push it with audio file processing.  Here's what I've been using since Edgy:

6GB for "/"
0.5 GB for swap
the rest of it for "/home"

:guitar:

---

