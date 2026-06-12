---
title: "Apt Cache Limit"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by tachyon4 on 2012-02-04
I had been adding sources to sources.list.  Then I updated, tried to install (via apt-get) and received the following error:

E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing riece (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.offensive-security.com_dists_pwnsauce_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

After some googling around, I learned how to fix the problem by adding the line

APT::Cache-Limit "100000000";

to etc/apt/apt.conf.d/70debconf.  It worked.  I no longer get the error; I can install as usual. :D

I'm just curious what happened and what the solution means.

---

### Post by jerrrys on 2012-02-06
[LIST]
[*]apt-get autoclean  This command  removes .deb files for packages that are no longer installed on your  system.  Depending on your installation habits, removing these files  from */var/cache/apt/archives* may regain a significant amount of diskspace.
[*]apt-get clean The same as above, except it removes ***all***  packages from the package cache.  This may not be desirable if you have  a slow internet connection, since it will cause you to redownload any  packages you need to install a program.

[LIST]
[*]The package cache is in */var/cache/apt/archives* .  The command 
du -sh /var/cache/apt/archives will tell you how much space cached packages are consuming.
[/LIST]
[*][http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apt-cache+limit&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apt-cache+limit&sa=Search&cof=FORID:9)
[/LIST]

---

### Post by smartgenes on 2012-07-15
Also, for newbies like me, you must sudo vi /etc/apt/apt.conf.d/70debconf
from the terminal (without sudo you won't be able to write the file)

When in vi (viewer), hit [a] (to append), then type or paste

APT::Cache-Limit "100000000";

then [ESCAPE] :w [ENTER] (to write changes), then you can :q (quit)

---

