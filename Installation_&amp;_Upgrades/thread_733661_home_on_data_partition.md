---
title: "/home on data partition"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Kiri on 2008-03-24
Hi, I am about to install ubuntu and I want to set up a /home directory on a separate partition. But I want to have the partition that /home is on also used for other data storage (also accessed from XP). 
Note that /home will NOT be the only directory on the partition. Is this ok?

Assuming it is ok, can I set up this way when I first install? Or do I need to go through the process of moving and setting up the new /home after installing ubuntu?


Last question: If I want to install another distro also, can I put it's /home on the same partition as the ubuntu /home, but under a different directory? (I don't want two distros to share the same /home, I just want to put both /home 's on the same partition)


Thanks for advice. Sorry if it was confusing

---

### Post by housam on 2008-03-24
Why don't you make a ntfs format partition as a data storage partition that can be seen from all distros you have including windows?

---

### Post by Kiri on 2008-03-24
> Why don't you make a ntfs format partition as a data storage partition that can be seen from all distros you have including windows?

I was thinking of doing that, but then where does my /home go?
I think putting /home on an ntfs partition might cause some problems...

---

### Post by housam on 2008-03-24
Ntfs format partitions are very much accessable from Gutsy without any problems.beside making a separate data storage partition will protect your data from system craches because you don't have to assign it during the installation and can be used from both operating systems.

---

