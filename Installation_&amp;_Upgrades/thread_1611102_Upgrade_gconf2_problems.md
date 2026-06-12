---
title: "Upgrade gconf2 problems"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Wtwine on 2010-11-01
Hi

I upgraded netbook edition Lucid to Maverick and ended up with a busted system that does not allow upgrading, adding or removing packages (posted [here]("http://georgia.ubuntuforums.org/showthread.php?t=1602289")).  There seems to be a dependency issue with gconf2.  I have checked sources.list, and all seems fine.

Here is a portion of the error message I get:
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 162, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 121, in read_entries
    for line in file(filename):
IOError: [Errno 21] Is a directory: '/usr/share/gconf/mandatory/share'
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2)

I have tried the following but none fix it:
sudo dpkg --configure -a
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get --fix-missing upgrade
sudo apt-get -f install

Any ideas?

---

