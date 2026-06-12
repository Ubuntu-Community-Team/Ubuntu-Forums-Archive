---
title: "unmet dependencies during upgrade"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by uinarffraniu on 2011-11-01
Hi all, I've tried an update and got an error message. Useful suggestions on how to resolve the issue would be appreciated. Error messages below

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gnome-terminal : Depends: gnome-terminal-data (>= 3.0) but 2.32.1-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.

when I run 

sudo apt-get -f upgrade
(...)
The following packages will be upgraded:
  gnome-terminal-data
(...)
Preparing to replace gnome-terminal-data 2.32.1-0ubuntu3 (using .../gnome-terminal-data_3.0.1-0ubuntu3_all.deb) ...
Unpacking replacement gnome-terminal-data ...
dpkg: error processing /var/cache/apt/archives/gnome-terminal-data_3.0.1-0ubuntu3_all.deb (--unpack):
 failed to stat (dereference) existing symlink `/usr/share/omf/gnome-terminal/gnome-terminal-cs.omf': Input/output error
Processing triggers for gconf2 ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-terminal-data_3.0.1-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I get this error message. No clue how to proceed, please help

---

