---
title: "Upgrade wxGTK to 2.8*"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by IdioticCreation on 2007-06-12
I'm using Code::Blocks compiler, and found that there is a bug regarding old versions of wxGTK (That caused the program to crash).  I'm not sure how to upgrade, but on the wxWidgets Web site it said to add this:
deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) dapper main

However I don't really know what it means.  I tried just going to that url and it had several .deb packages.  I would be grateful if someone could assist me in upgrading my wxGTK to version 2.8.4

Thanks,
David

---

### Post by moma on 2007-06-13
On the command line, open and edit the /etc/apt/sources.list file 
$ sudo gedit /etc/apt/sources.list 

Use gedit editor if you run Ubuntu.  Use kate or nano editor if you run X/Kubuntu.

Add this line to that file

```
deb http://apt.tt-solutions.com/ubuntu/ feisty main
```

Replace word **feisty** with **edgy** if you run Ubuntu 6.10.

Save the file and run commands
$ wget [http://www.tt-solutions.com/vz/key.asc](http://www.tt-solutions.com/vz/key.asc)
$ sudo apt-key add key.asc

$ sudo apt-get update 
$ sudo apt-get dist-upgrade 

This is how to install Code::Blocks C/C++ IDE on Ubuntu
[http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)
---------------------------------------------

Gutsy Gibbon's developers must upgrade wxWidgets to version 2.8.4.   The current version 2.8.1 in Feisty is very buggy.

---

