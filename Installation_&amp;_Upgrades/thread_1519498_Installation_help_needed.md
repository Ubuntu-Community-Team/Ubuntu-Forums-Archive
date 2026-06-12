---
title: "Installation help needed"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by masterskop on 2010-06-28
Hi,

I have a problem after an installation of Lucid.  I have the following partitions:

/linux swap
/home
/

I kept the /home partition during the manual phase of the installation and did not format that partition.  After the installation process of Lucid, everything is slow.  Probably not all programs are loaded?  Do I need to do an update/upgrade?  I do have the old sources.list file and an installed-applicaitons.txt file as well.

thanks

---

### Post by dino99 on 2010-06-28
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

check that your driver is activated (system admin hardware driver)

---

