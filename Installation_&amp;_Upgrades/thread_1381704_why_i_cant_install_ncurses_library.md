---
title: "why i cant install ncurses library?"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by tpanduka on 2010-01-15
panduka@ubuntu:~$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libncurses5-dev
0 upgraded, 1 newly installed, 0 to remove and 180 not upgraded.
[COLOR=Red]E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory[/COLOR]
panduka@ubuntu:~$ 

why i cant install ncurses library?

---

### Post by tpanduka on 2010-01-15
:Ptake a look @ above programme.
After running the commands if u get errors like this 
use following....

:popcorn:
Ok Ok i found the way to properly install ncurses library in ubuntu 9.10
if you cant get it with terminal comands
search it @system/administration/synaptic pakage manager
After visiting there in quick search type libncurses.
it will show u the libncurses files in the system.
Mark it & press apply button.
it will show u some options like install,upgrde,etc...
use install option
it will download some files fom the archive
then make it install
now u are ready to go...
good day guys...:D

---

### Post by howefield on 2010-01-15
> **tpanduka said:**
> [COLOR=Red]E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory[/COLOR]

You can only use one package manager at a time, so you probably had Synaptic Package Manager or similar open at the same time as trying to install via terminal.

Close them and you'll be able to install from terminal.

I see from your second post you got it installed, but just so you know :)

---

### Post by tpanduka on 2010-01-15
Thanx dear...
Now it's working

---

### Post by howefield on 2010-01-15
> **tpanduka said:**
> Thanx dear...

You're welcome.

> Now it's working

I know.

I wanted you to know what you were doing wrong. Better luck next time ;)

---

