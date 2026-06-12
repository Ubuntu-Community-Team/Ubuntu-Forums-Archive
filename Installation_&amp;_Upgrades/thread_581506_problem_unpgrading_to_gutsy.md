---
title: "problem unpgrading to gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by corson87 on 2007-10-19
yesterday i tried updating from feisty to gutsy but  before the update manager was able to finish downloading all the files, my internet connection died. i ended up restarting my pc, and now when i try to run update manager i get the following message:

'E: Dynamic MMap ran out of room, E: Dynamic MMap ran out of room, E:Error occurred while processing xblast (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


i tried googling it but i cant find anything that helps me. 

thanks!

---

### Post by opm8 on 2007-10-19
If I recall correctly I've seen this kind of thing before.

It goes something like this (I'm paraphrasing from memory):  apt has a "feature" where it can only cache so much data from its repositories. It sounds like you have too many in your /etc/apt/sources.list.  Try removing the custom sources to get the list a little shorter, do a  'sudo apt-get update' and try your install again.

opm8

---

### Post by corson87 on 2007-10-19
i tried deleting some of them but it still gives me the same exact message. im stumped

---

### Post by corson87 on 2007-10-19
the solution i used was to delete all the gutsy entry on the sources.list

now everything works!

---

### Post by joepotter on 2007-10-19
> **corson87 said:**
> yesterday i tried updating from feisty to gutsy but  before the update manager was able to finish downloading all the files, my internet connection died. i ended up restarting my pc, and now when i try to run update manager i get the following message:

'E: Dynamic MMap ran out of room, E: Dynamic MMap ran out of room, E:Error occurred while processing xblast (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


i tried googling it but i cant find anything that helps me. 

thanks!


You need to do the update from the command line in the old fashioned Debian way.

1) use Ctrl+Alt+F4 to get a virtual terminal

2) try 'sudo dpkg --configure -a'
(this will finish installation and configuration of the half done stuff)

3) 'sudo apt-get dist-upgrade'

4) pray. :-)

You may have to also use 'sudo apt-get dist-upgrade -f' and you might have to use dpkg more than once.

Unfortunately, you may also have to ask about the "force" feature of dpkg if a stubborn package gets itself half installed.

Good  luck.

---

