---
title: "Installing Ubuntu"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by Bert987 on 2013-04-25
is it better to install Ubuntu and let Ubuntu  configure the file system? or  Example i usually add swap file 2 X ram & root 10 GB and 15 GB Home  ext4 i think. I install 12.10 my usually way man is it slow i install gnome 3 that made a huge difference i the speed of my system.
 
Sys Spec

intel 6420 2.13 GH Dual core
8 GB ram 
250 GB Standard Sata drive 
Ati Video card

---

### Post by Bucky Ball on 2013-04-25
*Thread moved to **Installation & Upgrades**.*

You don't need 2x the RAM and not sure why /home is so small.

If you go for a custom, manual partitioning setup, you certainly won't get anything like that if you let Ubuntu do it for you. It won't give you a separate /home, for instance. All in / and it will make / on any free space it finds (or wipe your whole drive and use that if you instruct it to). Not ideal.

Not sure what you mean when you ask 'let Ubuntu configure the file system ...' You mean the file system of the partitions you're creating? They'll be EXT4. Use that anyway, regardless how you do it.

---

### Post by carl4926 on 2013-04-25
> **Bert987 said:**
> is it better to install Ubuntu and let Ubuntu  configure the file system? or  Example i usually add swap file 2 X ram & root 10 GB and 15 GB Home  ext4 i think. I install 12.10 my usually way man is it slow i install gnome 3 that made a huge difference i the speed of my system.
 
Sys Spec

intel 6420 2.13 GH Dual core
8 GB ram 
250 GB Standard Sata drive 
Ati Video card
15GB is not much space for /home unless you are storing data elsewhere.

Ubuntu doesn't create a separate /home by default
So if you prefer it, do it manually and assign mount points during install
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png)
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png)

---

