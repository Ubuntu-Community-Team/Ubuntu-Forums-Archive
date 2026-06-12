---
title: "How to Upgrade Wubi installed Ubuntu11.10 in offline"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Praveen_zen on 2012-06-08
Hi,
I have installed ubuntu 11.10 in Wubi as a alongside to windows 7. Now new release of Ubuntu12.04 has came. I don't have a high speed net connection to upgrade 11.10. But i have live Cd of Ubuntu12.04. Is it possible to upgrade Wubi installed ubunutu in offline?

---

### Post by bcbc on 2012-06-08
Yes 

You need the alternate CD ISO (not the live CD): [https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD](https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD)

You should also review [this]("http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-upgrade-wubi-install.html"), in particular note that you need 3GB of free space.

Also if you have graphics drivers manually installed (not from the repos) then it seems to be recommended to remove them prior to upgrade and reapply afterwards.

---

### Post by Praveen_zen on 2012-06-12
Thanks. I will try and reply

---

### Post by Praveen_zen on 2012-06-12
Its working.

---

