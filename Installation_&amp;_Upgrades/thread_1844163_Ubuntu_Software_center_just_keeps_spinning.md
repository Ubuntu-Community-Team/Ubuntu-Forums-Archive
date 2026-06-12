---
title: "Ubuntu Software center just keeps spinning"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by Pullapulla on 2011-09-14
Hey, I'm quite new to Linux and Ubuntu. I installed 11.04 a couple of months ago and all was fine but all of a sudden my ubuntu software center doesn't work anymore.When I try to do something it just starts loading and never stops. One forum suggested this fix:

sudo apt-get update

terminal started to open lots of files but ended up with this:


Fetched 2,754 B in 1s (1,878 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/fi.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

sudo apt-get upgrade gave me the same resault.

Has anybody had similar problems?

---

### Post by Rubi1200 on 2011-09-14
Hi and welcome to the forums :)

Open a terminal and copy/paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

---

