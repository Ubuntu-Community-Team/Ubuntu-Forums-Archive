---
title: "installing ubuntu 9.10 on a previous installation with a separate /home partition"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by srirammanoj on 2009-12-18
Hi,
I had ubuntu 9.4 on my laptop with a separate /home partition.
I decided to install 9.10 instead of upgrading.
I configured the / partition same as the previous one and went ahead with the installation.
The installation went ok but the problem is that it created a new /home inside the / partition.
The original /home partition is now treated like a separate drive which has to be mounted.
My question is,
Can i change the home directory in the menu ? Will it work ? Because the /home partition needs to be mounted after every restart.
Or should i have configured /home during the installation (i was afraid that the new installation might wipe out the data and consequently did nothing there) ?

---

### Post by unmole on 2009-12-18
You should have configured the /home partition during install. However make sure you don't change the File System. The default in Jaunty was Ext3 and in Karmic it is Ext4. If you want to try a reinstall, mark the hape partition as /home and use as Ext3 and _**do not**_ fromat. 

If you want to experiment, you could try adapting this tutorial as you already have the home partition with all your files. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by srirammanoj on 2009-12-18
Thank you very much.
It worked like a charm.

---

