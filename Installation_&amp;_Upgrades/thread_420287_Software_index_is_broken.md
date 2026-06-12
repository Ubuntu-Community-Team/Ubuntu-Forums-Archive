---
title: "Software index is broken"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by sirtom on 2007-04-23
Clean install of Feisty. I see 3 updates to install but i get this: 

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


sirtom@estate:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
0 upgraded, 0 newly installed, 9 to remove and 3 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9171kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Bus error (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 135
Removing libcairomm-1.0-1 ...
Bus error (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libdebconfclient0 ...
Bus error (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libdebian-installer4 ...
Bus error (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libdiscover1 ...
Bus error (core dumped)
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libfuse2 ...
Bus error (core dumped)
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 135
Removing libglibmm-2.4-1c2a ...
Bus error (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 135
Removing libntfs9 ...
Bus error (core dumped)
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 135
Removing xfsprogs ...
Bus error (core dumped)
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 135
Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)

where do i start fixing this? its not mentioned in my shiny new book lol

---

### Post by sirtom on 2007-04-24
Bump! :-\" 

OK what about "subprocess post-removal script returned error exit status 135"

...where do look up these codes, Google returns nothing.

---

### Post by sirtom on 2007-04-25
Anyone?

I am posting in the wrong section? Or the wrong website??

---

### Post by sunflower on 2007-06-11
I've got the same prob. Haven't received any help yet :) If I do i'll let you know..

---

