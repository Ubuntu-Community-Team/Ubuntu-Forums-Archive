---
title: "no auto update in lts server default config"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by doru001 on 2010-03-03
There is no auto update in lts server text mode, default configuration since I installed it 6 months ago! Please pay attention to this important issue, and answer here: 

[http://ubuntuforums.org/showthread.php?t=1415700](http://ubuntuforums.org/showthread.php?t=1415700)

---

### Post by doru001 on 2010-08-07
I have installed unattended-upgrades and anacron, but still my Ubuntu 8.04 lts server is not automatically upgraded. 

What else should I do?

---

### Post by dino99 on 2010-08-07
see the synaptic settings

---

### Post by doru001 on 2010-08-08
> **dino99 said:**
> see the synaptic settings
I don't have synaptic installed, I don't have GUI installed, I use apt-get & comp. What settings should I change and what apt-* conf file should I use to set them?

---

### Post by dino99 on 2010-08-08
you might find the good settings there:

[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)

---

### Post by doru001 on 2010-08-09
> **dino99 said:**
> you might find the good settings there:

[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)

The apt suite of tools does not provide auto update, this is a cron job. Why doesn't unattended-upgrades do its job? What is /etc/cron.daily/apt doing in this world?

---

### Post by doru001 on 2010-08-31
> **dino99 said:**
> you might find the good settings there:

[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)

APT::Periodic:: options are not described in the apt.conf manual, they are offered by unattended-upgrades: 

The solution to automatic upgrades in Ubuntu 8.04 lts server: 
I installed the unattended-upgrades and anacron packages (anacron because my server is not always up). 
Following /usr/share/doc/unattended-upgrades/README, I put in /etc/apt/apt.conf: 
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```I created apt.conf with permissions: -rw-r--r-- 1 root root

According to the default settings in: 
```
/etc/apt/apt.conf.d/50unattended-upgrades
```which is also mentioned in: 
```
/usr/share/doc/unattended-upgrades/README
```only the security updates are performed automatically. For the others, you should uncomment the ...-updates line. 
unattended-upgrades keeps a log in: 
```
/var/log/unattended-upgrades/
```See also: 
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

---

