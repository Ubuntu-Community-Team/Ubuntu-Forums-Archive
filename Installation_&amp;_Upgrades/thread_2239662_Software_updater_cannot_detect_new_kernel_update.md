---
title: "Software updater cannot detect new kernel update"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by medo-tareq on 2014-08-15
i use ubuntu 14.04 tried to update the kernel from 3.13.0-_33_-generic to _**3.13.0-34-generic**_ but it cannot detect the new update i changed the server but the same result :(

---

### Post by mikewhatever on 2014-08-15
It's probably nothing major, some mirrors are a few days behind the main one. Can you post the output of <cat /etc/apt/sources.list> for review.

---

### Post by kc1di on 2014-08-15
Go to a terminal and type the following see if that will work?

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by stjohn-michael on 2014-08-15
> **kc1di said:**
> Go to a terminal and type the following see if that will work?

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Do this if nothing
sudo apt-get linux-lts-trusty

---

### Post by kansasnoob on 2014-08-15
> **stjohn-michael said:**
> Do this if nothing
sudo apt-get linux-lts-trusty

**[COLOR="#FF0000"]*NOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!!!*[/COLOR]**

The OP said, "i use ubuntu 14.04".

Look, I'm also running 14.04:

```
lance@lance-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
lance@lance-desktop:~$ apt-cache policy linux-lts-trusty
N: Unable to locate package linux-lts-trusty

```

Don't suggest things you're not sure of!!!!!!

---

### Post by ajgreeny on 2014-08-15
The update-manager (or software-updater) takes account of the "phased updates" system whereby only a percentage of users get all the updates immediately, and they are then rolled out in succession over a few days.  This allows any package updates that may cause problems to a few users to be more fully investigated and withdrawn if necessary, avoiding any major problems which, although they may be very rare, have happened in the past.

This is a feature of the update manager, not a bug of any kind, but it can be over-ridden if you wish to by using either synaptic package manager, or the command line **sudo apt-get update**.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-phased-updates](https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-phased-updates)
[http://askubuntu.com/questions/369722/update-manager-does-not-show-all-updates](http://askubuntu.com/questions/369722/update-manager-does-not-show-all-updates)

---

### Post by kansasnoob on 2014-08-15
> **ajgreeny said:**
> The update-manager (or software-updater) takes account of the "phased updates" system whereby only a percentage of users get all the updates immediately, and they are then rolled out in succession over a few days.  This allows any package updates that may cause problems to a few users to be more fully investigated and withdrawn if necessary, avoiding any major problems which, although they may be very rare, have happened in the past.

This is a feature of the update manager, not a bug of any kind, but it can be over-ridden if you wish to by using either synaptic package manager, or the command line **sudo apt-get update**.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-phased-updates](https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-phased-updates)
[http://askubuntu.com/questions/369722/update-manager-does-not-show-all-updates](http://askubuntu.com/questions/369722/update-manager-does-not-show-all-updates)

+1! The word *phased* refused to come to mind :redface:

I have three machines connected to the same LAN and they do not always get the same updates at the same time. Sometimes patience is a true virtue.

---

### Post by medo-tareq on 2014-08-15
i don't think that because the same  happened before and after reinstalling ubuntu  it caught the latest update :(

---

### Post by medo-tareq on 2014-08-15
> **kc1di said:**
> Go to a terminal and type the following see if that will work?

```
sudo apt-get update
sudo apt-get dist-upgrade
```


i did that and there is no result

---

### Post by medo-tareq on 2014-08-15
if the update is randomly then why it will be available after installing ubuntu again!!

if that okay i will wait .no problem although my friend  installed ubuntu two days ago and installed the next kernel

---

### Post by ajgreeny on 2014-08-15
> **medo-tareq said:**
> if the update is randomly then why it will be available after installing ubuntu again!!

if that okay i will wait .no problem although my friend  installed ubuntu two days ago and installed the next kernel

Perhaps your friend is not using the exact same servers for his repositories, as not all servers get the packages at the same time.

---

