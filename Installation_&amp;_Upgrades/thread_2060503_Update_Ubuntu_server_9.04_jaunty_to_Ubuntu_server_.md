---
title: "Update Ubuntu server 9.04 jaunty to Ubuntu server 12.04.1 LTS"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by adsnetwork on 2012-09-20
Hi Guys

I have been pulling my hair out with this. I have servers in a DC remotely i tried Updating the servers but cant get 9.04 jaunty any higher. 

These are the commands I ran: 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install update-manager-core

It does not go any higher ;( If I should modify the source list what should it be? 
Is it even possible to upgrade directly from 9.04 jaunty to Ubuntu server 12.04.1 LTS

Please any help would be gladly appreciated 

:D

---

### Post by cogier on 2012-09-20
Updating the OS can take hours. Your OS 9.04 is quite a few upgrades from 12.04.

You would need to Upgrade from 9.04 to 9.10 then to 10.04 LTS and then to 12.04 LTS. This is NOT recommended.

Get yourself a fresh CD of 12.04 and start a nice fresh install.

---

### Post by grahammechanical on 2012-09-20
+1 to what cogier has said.

Ubuntu 9.04 is not an LTS release. We can upgrade from one LTS to another LTS. So, we can go from 10.04 to 12.04 and by-pass 10.10, 11.04, and 11.10.

But if we are using a non-LTS release then we must upgrade step by step, release by release.

There is a massive difference between 10.04 and 12.04 and not just in looks (which you will not have with a server edition) but with the underlying libraries. So, I guess that there is even more difference between 9.04 and 12.04.

Think seriously about fresh installing.

Regards.

---

### Post by adsnetwork on 2012-09-20
Guys I got to 

root@home:/etc/apt$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

But any further than this it just does not work.. ;(

When i do sudo do-realease-upgrade i get:

Error during commit: Internal error could not perform immediate configuration (2) on until-linux
Restoring original system state..

Any advise ?

---

### Post by snowpine on 2012-09-20
Welcome to the forums!

Any advise? you ask...

1. Back up and do a fresh reinstall. This will be the quickest and most reliable in the long run.

2. If you must upgrade for whatever reason, then you need to follow the EOL instructions here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

