---
title: "Preparation for 10.04"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2010-04-25
I have decided after looking through several posts that I am going to do a clean install when 10.04 is released.  I have a couple of questions though.  I am going to be using a separate partition for my HOME folder.  Should I format this said partition in ext4 BEFORE I move my HOME folder since I will be using ext4 with the clean install, and if so, can I move it there or will I need to restore a backup of my HOME folder to this partition after the clean install?  Also, will I need to reinstall all my programs?  I have found several methods to do this that seem pretty good and fairly easy.  I am thinking reinstalling might be a better option anyway.  Any advice input would be welcomed

---

### Post by jocko on 2010-04-25
> **scpatl4now said:**
> Should I format this said partition in ext4 BEFORE I move my HOME folder since I will be using ext4 with the clean install, and if so, can I move it there or will I need to restore a backup of my HOME folder to this partition after the clean install?
Yes. You need to format the partition to ext4 first, then copy your home folder to it.
Just to be clear: Just copy your and any other users home directory (/home/[COLOR=Blue]username[/COLOR]) to the new partition. Don't move the entire /home folder (as that would make it mount as /home/home/username, which would not work).

During the install just choose the advanced partition setup, set one partition for the root file system (/). This needs to be formatted. Then set your new /home partition to mount as /home, but do **not** format it.

> **scpatl4now said:**
> Also, will I need to reinstall all my programs?  I have found several methods to do this that seem pretty good and fairly easy.  I am thinking reinstalling might be a better option anyway.  Any advice input would be welcomed
Yes. You need to reinstall everything. Nothing will be left of your old install.
There are a few ways to generate lists of all installed packages. One simple way is to open up synaptic, and in the file menu click "save selections as".
Then after you have installed 10.04, just open up synaptic and click "read selections", direct it to the file you saved with "save selections", then "apply" to install everything.

---

