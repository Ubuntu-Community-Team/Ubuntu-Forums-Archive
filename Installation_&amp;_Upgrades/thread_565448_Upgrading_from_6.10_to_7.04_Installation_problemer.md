---
title: "Upgrading from 6.10 to 7.04 Installation problem/error message"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by jpcrow on 2007-10-02
Update manager tells me this:


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing wesnoth-editor (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I haven't updated ubuntu in a long time... 3.65 GB of free space 

Windows/Linux partitions dual boot

What does this message mean, and how do get back to updating my system to 7.04? 

Thanks in advance,

-jpc

---

### Post by jpcrow on 2007-10-02
Bump

---

### Post by Seisen on 2007-10-02
Edit your /etc/apt/apt.conf  and add this to it.

```
APT::Cache-Limit "8388608
``` also run ```
sudo apt-get autoclean
``` that will also clean out the archive.

---

