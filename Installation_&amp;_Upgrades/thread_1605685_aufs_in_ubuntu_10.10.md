---
title: "aufs in ubuntu 10.10"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by j0hnd0342 on 2010-10-25
Hello

  I have just installed ubuntu 10.10 32 bit on my server but I am having a problem.

  Earlier I have always used aufs to make 4 folders appear as one 2 the users

  For example if i want the folders eks1-4 to appear as the folder eks to the users 
mount -t aufs -o br=eks1:eks2:eks3:eks4 none eks

  My problem is that aufs does'nt seem to be in the repos any longer. Does anyone know if this is true or is it just me making some mistake when trying to install it?

  I am also looking for an alternative to aufs.

---

