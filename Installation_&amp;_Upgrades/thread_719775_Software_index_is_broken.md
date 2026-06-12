---
title: "Software index is broken"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by laura eznarriaga on 2008-03-09
"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

This is the response I am getting from update manager. After following the above the Synaptic method just doesn't work at all. The Terminal method I get this:

"russ@FishTank:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
gnome-btdownload
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 496kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 101476 files and directories currently installed.)
Removing gnome-btdownload ...
dpkg: error processing gnome-btdownload (--remove):
cannot remove file `/usr/share/man/man1/gnome-btdownload.1.gz': Not a directory
Errors were encountered while processing:
gnome-btdownload
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Any advice will be most welcomed. Using "Gutsy"
Many thx in anticipation

---

### Post by oldos2er on 2008-03-09
Have you tried manually deleting the file /usr/share/man/man1/gnome-btdownload.1.gz ?

---

