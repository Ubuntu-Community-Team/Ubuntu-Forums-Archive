---
title: "what to expect with a do-release-upgrade?"
date: 2015-04-12
forum: Installation &amp; Upgrades
---

### Post by ubu_Leno on 2015-04-12
Hi 

I am wonder is anybody can tell me about the do-release-upgrade process, I will need to do a upgrade from Server 10.04 LTS to 12.04 LTS and am wondering what I should expect?

The server has service postfix and apache with mysql.

My plan is to do following with screen/ssh (but console access close)

1. apt-get update
2. apt-get upgrade
3. reboot
4. do-release-upgrade
4.1 most likely keep existing configs and fix after upgrade finished
5. reboot
6. done?


Along with with question on general upgrade proccess, I have backups of db but i am wonder what happens with mysql db during update, are all database dropped and I need to re-add or should they be kept?

---

### Post by dino99 on 2015-04-12
in theory, upgrading from LTS to LTS is well tested; but we often get bugs report of all kind because the testing have not been done intensively enough.
that said, a fresh install is often more secure and does not take more time.

about your settings/database/... i suppose you can backup them first, and are stored into /home partition or somewhere outside the system partition. So take care to avoid formating these precious partition(s). But again old partitionning can have issue, which newer parted have fixed, so the better place for old things is often the museum.

---

### Post by ubu_Leno on 2015-04-12
> **9d9 said:**
> 
that said, a fresh install is often more secure and does not take more time.


Ideally yes but for the particular host i am stuck doing inplace. so just try to find out and prepare for what can happen.

---

