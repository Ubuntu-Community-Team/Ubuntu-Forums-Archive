---
title: "cron's /etc/cron.daily/apt not upgrading"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by doru001 on 2010-02-25
It seems that cron is not upgrading my Ubuntu 8.04 LTS Server, no GUI installed. I changed /etc/crontab and watched apt running:
```
ps -A | grep apt 
```showed it for a long time, 
```
sudo tcpdump tcp
```showed communication with canonical sites, 

but: 
```
top
``` did not show any apt using CPU 
```
/var/log/dpkg.log
``` is empty, excepting some installs I did last week 
```
sudo apt-get -s upgrade
``` shows a large number of packages to be upgraded. 

Please give me some advice. 

Other threads: 
[http://ubuntuforums.org/showthread.php?t=646484&highlight=cron+apt+server+lts+dpkg.log](http://ubuntuforums.org/showthread.php?t=646484&highlight=cron+apt+server+lts+dpkg.log)

---

### Post by doru001 on 2010-02-26
Ubuntu's current LTS server does not upgrade packages automatically as it should! Please, any comment.

---

### Post by doru001 on 2010-02-27
Auto update does not work in its original configuration, and nobody cares. All that work to provide security updates is lost because of some script.

---

