---
title: "Firefox Installation Help"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by rex689 on 2013-04-17
I am having trouble installing Firefox. I tried it both through the terminal and the package manager and I get a similar error.


The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 393 not upgraded.
1 not fully installed or removed.
Need to get 0 B/24.5 MB of archives.
After this operation, 51.3 MB of additional disk space will be used.
(Reading database ... 104548 files and directories currently installed.)
Unpacking firefox (from .../firefox_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_i386.deb (--unpack):
 trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 12.04ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I had kubuntu before, this is my third time actually installing it, and never had this problem. Why is it having this problem?
If needed I installed it from a flash drive. I could reinstall if needed.

Thanks for any help in advance.

---

### Post by cortman on 2013-04-17
Hi, welcome to the forums!

Try running

```
sudo apt-get cleansudo rm -r /var/lib/apt/lists/*
sudo touch /var/lib/apt/lists/lock
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update

```

These will often fix such problems.

---

### Post by rex689 on 2013-04-17
Sorry, the terminal has to be the harderst thing for me to get.

When I type in the first line, i get this error.

sudo apt-get cleansudo rm -r /var/lib/apt/lists/
E: Command line option 'r' [from -r] is not known.

I usuall use the terminal to get some programs or apt-get update option and that is it.

Thanks for the help.

---

### Post by ibjsb4 on 2013-04-17
Thats funny, cortman just made a typo

sudo apt-get clean

sudo rm -r /var/lib/apt/lists/*

---

### Post by rex689 on 2013-04-17
Thanks for the help! I got firefox now.

---

### Post by ibjsb4 on 2013-04-17
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by xinbye on 2013-04-23
if you can't install
you can use the method in : [http://forum.ubuntuusers.de/topic/firefox-installation-bricht-ab/#post-5499257](http://forum.ubuntuusers.de/topic/firefox-installation-bricht-ab/#post-5499257)
i am successed

---

### Post by cortman on 2013-04-23
Well, FTR- the OP made the typo- there needs to be a space between "rm" and the "-r" option.

---

