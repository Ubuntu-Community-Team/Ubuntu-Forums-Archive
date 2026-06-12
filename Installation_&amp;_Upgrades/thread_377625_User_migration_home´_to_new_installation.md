---
title: "User migration /home´ to new installation"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by leeportnoff on 2007-03-06
I would like to move my Ubuntu 6.06  /home  directory and user accounts to a fresh 6.10 install.  

In the past I have copied files, created new users, gave new users recursive ownership and re-entered evolution pop & smtp account information.

There must be an easier way.

ubuntu,
-Lee

---

### Post by Kateikyoushi on 2007-03-06
This solution seems easier. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by leeportnoff on 2007-03-06
I would like to move my Ubuntu 6.06  /home  directory and user accounts to a fresh 6.10 install.  

In the past I have copied files, created new users, gave new users recursive ownership and re-entered evolution pop & smtp account information.

There must be an easier way.  Please do tell; or point me to some documentation.  Many Thanks.

ubuntu,
-Lee

---

### Post by dannyboy79 on 2007-03-06
after you move your /home directory to it's own partition, than you simply reuse it. make sure new edgy DOESN'T format that partition, just lablels it as your /home mount point. you'd be able to do this with the alternate install cd and using the custom partitioning when you get to the partition part., just uncheck the format button. if you use the same exact username and whatnot I don't see why this would work. As a precautionary measure you should back up your /home partition prior to doing edgy install. see my sig for 2 tools that are great for backing up partitions instead of using tar or dar or sbackup, cause all those are dir and file backup tools, where as partimage just backs up the entire partition. it's a fail safe in case edgy overwrites your existing home partition but it shouldn't if you uncheck the format check box using the alt install cd. good luck

---

### Post by zvacet on 2007-03-06
If I understand you correctly you don´t have separate home partition.If that is the truth look this
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
When you do that you can re-install or make clean install and your home directory will be safe.

---

### Post by bapoumba on 2007-03-07
@ leeportnoff: I've merged your other thread in this one :)

---

