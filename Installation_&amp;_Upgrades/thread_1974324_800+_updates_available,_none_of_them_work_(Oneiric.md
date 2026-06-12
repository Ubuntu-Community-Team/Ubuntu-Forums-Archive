---
title: "800+ updates available, none of them work (Oneiric 32-bit)"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by djehuti on 2012-05-05
Hi everyone, sticking with 11.10 for now. This problem showed up about 3 weeks ago, and no matter what I've tried, nothing seems to work. When I boot Ubuntu the update window comes up and says I have anywhere between 808 and 824 updates available (today, 814), and says this:
> 
Not all upgrades can be installed

Run a partial upgrade, to install as many updates as possibleI have the choice to do nothing or run a partial upgrade. I try that, and then it says,

> An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later."For fun I tried 'sudo apt-get upgrade' and got this:

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?It's definitely not a transient problem, that's for sure. What's wrong with my upgrades? :confused:

---

### Post by dino99 on 2012-05-06
After booting, if you see again the update message for installing/upgrading packages, refuse it, then open a terminal and run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

sudo apt-get install synaptic (if it is not already installed )
sudo synaptic

on the left pane, select "status" and from the top menu, set package details visible in the window.
now you can hit "reload" to get the available updates; and instead installing all of them in a row, only install a few at a time. Then you will know which one is a partial update: mainly its due to missing new package you need to install first, or it will popup with details for removing something else.

---

### Post by djehuti on 2012-05-07
Thanks for the answer. I followed the instructions, and when I tried to update the packages in Synaptic, I got this error message:

> W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA

It's the same as I saw each time these last 3 weeks, so there must be some changed setting that needs to be reverted, I'm thinking. Is there some way to solve this?

---

### Post by wilee-nilee on 2012-05-08
> **djehuti said:**
> Thanks for the answer. I followed the instructions, and when I tried to update the packages in Synaptic, I got this error message:



It's the same as I saw each time these last 3 weeks, so there must be some changed setting that needs to be reverted, I'm thinking. Is there some way to solve this?

You have a Debian repo in Oneric?

Your sources list may be a bit messed up or you have added stuff that probably is not helping.

Post the out put of.

```
cat /etc/apt/sources.list
```

---

### Post by djehuti on 2012-05-09
Thanks for the reply. Here's the output:

```
# /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
deb http://debian.wgdd.de/ubuntu oneiric main restricted universe multiverse
deb-src http://debian.wgdd.de/ubuntu oneiric main restricted universe multiverse
deb http://ftp.de.debian.org/debian sid main

```

---

### Post by wilee-nilee on 2012-05-09
> **djehuti said:**
> Thanks for the reply. Here's the output:

```
# /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
deb http://debian.wgdd.de/ubuntu oneiric main restricted universe multiverse
deb-src http://debian.wgdd.de/ubuntu oneiric main restricted universe multiverse
deb http://ftp.de.debian.org/debian sid main

```

Hmm that is a rather strange list, here is what is stock when you make a stock source list from this website. Also the debian's should not be there.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```Now you have like one repo that is correct for Ubuntu in yours. I don't know what you have installed from debian, and if inserting this correct one in your sources.list is going to magically fix you.

How did you get here?

---

