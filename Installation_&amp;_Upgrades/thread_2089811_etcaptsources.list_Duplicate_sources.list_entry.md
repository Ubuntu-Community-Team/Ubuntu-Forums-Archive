---
title: "/etc/apt/sources.list Duplicate sources.list entry"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by diabolusss on 2012-11-30
This is my /etc/apt/sources.list:
```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb http://download.virtualbox.org/virtualbox/debian precise contrib
##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Opera - http://www.opera.com/
## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ stable non-free
```

When i run apt-get update i get:
```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

However, there is no duplicates!?

P.S. Of course, when i comment them error disappears

---

### Post by steeldriver on 2012-11-30
Do you have additional source files in the /etc/apt/sources.list.d/ directory maybe?

---

