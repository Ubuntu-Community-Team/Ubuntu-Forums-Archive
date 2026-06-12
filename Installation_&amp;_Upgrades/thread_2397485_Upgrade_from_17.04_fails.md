---
title: "Upgrade from 17.04 fails"
date: 2018-07-30
forum: Installation &amp; Upgrades
---

### Post by danik56 on 2018-07-30
I am trying to upgrade a system still running 17.04
I have modified /etc/apt/sources.list as advised to include only:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse


Then had no errors running:
 
apt update
apt upgrade
apt dist-upgrade

Then when attempting "do-release-upgrade" I get the following error:

Get:1 Upgrade tool signature [819 B]                                           
Get:2 Upgrade tool [1,257 kB]                                                  
Fetched 1,258 kB in 0s (0 B/s)                                                 
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'
Reading cache
Checking package manager
Can not upgrade 
An upgrade from 'zesty' to 'bionic' is not supported with this tool. 

Can I somehow upgrade first to 17.10 ?

---

### Post by Impavidus on 2018-07-30
Just try a fresh install of 18.04. It's faster and much more likely to succeed.

---

### Post by Autodave on 2018-07-30
17.04 was dead a while ago, so you cannot upgrade from it. 17.10 is also dead. So, at this point, you have to do a clean install of 18.04.  make sure you back up anything you need to an external source.

---

### Post by danik56 on 2018-07-31
I can obviously do a clean install of 18.04 but what about all the configured software that I have running ? Install everything from scratch ?  It will be a nightmare..

---

### Post by danik56 on 2018-07-31
When will 17.10 repositories move to old-releases ?

---

### Post by Impavidus on 2018-07-31
> **danik56 said:**
> I can obviously do a clean install of 18.04 but what about all the configured software that I have running ? Install everything from scratch ?  It will be a nightmare..Backup your config files and restore them after the fresh install, or keep them on a separate /home partition. Keep a list of all installed software and reinstall it (as far as you still need it) with a few clicks or commands. It shouldn't take more than an hour. The old configs aren't guaranteed to work, but you get that problem with an upgrade too. Sometimes things change.

> **danik56 said:**
> When will 17.10 repositories move to old-releases ?
Could be any moment, if they haven't moved already. It may depend on your mirror.

---

### Post by danik56 on 2018-07-31
For example, can IPTABLES rules be backed up and restored after fresh OS install ?

---

### Post by #&amp;thj^% on 2018-07-31
Yes of course:
```
iptables-save > /etc/iptables/rules.v4
```

These files can be loaded again with the command iptables-restore for IPv4.

```
iptables-restore < /etc/iptables/rules.v4
```

If you would also like to use IPv6 rules, these can be stored in a separate file.

```
ip6tables-save > /etc/iptables/rules.v6
```
I don't use ipv6 here on my system.(To note only)

---

### Post by jwinterton68 on 2018-10-08
Hi danik56
Where did you get to with your upgrade? I too need to upgrade from 17.04. In the past I have had more luck upgrading incrementally to get to a supported version than undertaking a clean install. Like you I want to avoid the hassle of configuring all my servers components again from scratch on 18.04. There should be (must have been at some point) an upgrade from 17.04 to 17.10. The installer only wants to jump me from 17.04 to 18.04 which it says of course is not supported. Any idea how to get it to upgrade to 17.10 instead. Then I will do 17.10 to 18.04 after that! At least, that is the theory.

---

### Post by oldos2er on 2018-10-08
Hi jwinterton68, please start your own thread,  danik56 hasn't returned to the forum since August.

---

