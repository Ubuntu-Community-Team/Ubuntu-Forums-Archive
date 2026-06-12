---
title: "Help with dual boot install on Netbook"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by 0007 on 2010-06-14
Hi, this is my first post.

I am running Windows 7 starter on my Samsung N150 Netbook. I have successfully installed Ubuntu on the 4 GB flash drive, and I have been running it for several weeks in the "try mode" without any problems. Now I decided to permanently install Ubuntu netbook edition on my computer from a flash drive. I am following this guide [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) and ran into a big problem on step #5 of the guide and step #4 of the installation. I am not getting the option of installing them side by side, choose between them each startup!!! Which is what I want to do... I am only getting the option of erase and use entire drive, and specify partitions manually. My goal is to keep Windows 7 on my netbook, and have an option of dual booting into either operating system. Please help me! :confused:  
p.s. I read in other guides that hardrive needs to be partitioned prior to install, and other people said it could be done within ubuntu install...so I did not re partition prior to install.

-0007

---

### Post by wilee-nilee on 2010-06-14
> **0007 said:**
> Hi, this is my first post.

I am running Windows 7 starter on my Samsung N150 Netbook. I have successfully installed Ubuntu on the 4 GB flash drive, and I have been running it for several weeks in the "try mode" without any problems. Now I decided to permanently install Ubuntu netbook edition on my computer from a flash drive. I am following this guide [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) and ran into a big problem on step #5 of the guide and step #4 of the installation. I am not getting the option of installing them side by side, choose between them each startup!!! Which is what I want to do... I am only getting the option of erase and use entire drive, and specify partitions manually. My goal is to keep Windows 7 on my netbook, and have an option of dual booting into either operating system. Please help me! :confused:  
p.s. I read in other guides that hardrive needs to be partitioned prior to install, and other people said it could be done within ubuntu install...so I did not re partition prior to install.

-0007

If you want to do a dual boot which I think is what your describing, rather then a wubi install from a running W7 setup, you need to shrink the W7 partition with the disk manager in W7 first. This should be done only in the W7 manager, defrag before doing this, then reboot it to make sure it is working. Then use the usb to install in the free space left by shrinking the W7 partition. 

Before doing anything though lets confirm the number of partitions you have, as there is probably at least two a recovery and the main OS run this and post it.
```
sudo fdisk -l
```
You can copy and paste that into a terminal if not it is not a 1 but a lower case L at the end.
Also confirm that you want a true dual boot=seperate OS not a wubi install.

---

### Post by 0007 on 2010-06-14
Yes I am trying to do a dual boot. Not Wubi! I am not getting the option to do side by side installation with windows 7 in the step 4 of the Ubuntu installation. 

I tried multiple times to restart the computer and boot, still no success. I do not want to mess with partitions if i am not going to be able to do side by side install.

---

### Post by garvinrick4 on 2010-06-14
> **0007 said:**
> Yes I am trying to do a dual boot. Not Wubi! I am not getting the option to do side by side installation with windows 7 in the step 4 of the Ubuntu installation. 

I tried multiple times to restart the computer and boot, still no success. I do not want to mess with partitions if i am not going to be able to do side by side install.
You can make your own partitions side by side no problem. Just need to see the the 

```
sudo fdisk -l
```  small L

We can then make your own partition first and then install manual and be done in a breeze. Also how much ram do you have. Copy and paste the results to this thread.

---

### Post by sriny1512 on 2010-06-14
As explained above by Wilee-Nilee, were you able to shrink the W7 partition and create a separate partition for Ubuntu. Another option you have, if you are not able to shrink the W7 partition is, 

- Backup all the important data you need. 

- Reinstall W7, while doing this break the partition and create a separate partition for Ubuntu. 

- After installing W7, start installing Ubuntu, select manual partitioning during installation and chose the empty partition you created for Ubuntu.

---

