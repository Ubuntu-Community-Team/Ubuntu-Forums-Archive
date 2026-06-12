---
title: "Failed to download reposiroty information"
date: 2017-07-14
forum: Installation &amp; Upgrades
---

### Post by MadMonkey1966 on 2017-07-14
Hi all, I just turned on my machine and it told me a new version was avaliable. I told it to go ahead, and go some errors. I just clicked and tried again, and now i get..

> Failed to download repository information
Check your internet connection.

Internet is fine as i have just popped onto Facebook....
I had a go in the Terminal (of which i am very not at all great), from what i have tried before...... and i got this.....

```
ian@ian-Dell-DM061:~$ sudo apt-get update

[sudo] password for ian: 

Sorry, try again.

[sudo] password for ian: 

Get:1 http://gb.archive.ubuntu.com/ubuntu yakkety InRelease

Err:1 http://gb.archive.ubuntu.com/ubuntu yakkety InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

Get:2 http://gb.archive.ubuntu.com/ubuntu yakkety-updates InRelease

Err:2 http://gb.archive.ubuntu.com/ubuntu yakkety-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

Get:3 http://gb.archive.ubuntu.com/ubuntu yakkety-backports InRelease

Err:3 http://gb.archive.ubuntu.com/ubuntu yakkety-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

Get:4 http://gb.archive.ubuntu.com/ubuntu yakkety-security InRelease

Err:4 http://gb.archive.ubuntu.com/ubuntu yakkety-security InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Fetched 2,379 B in 0s (14.9 kB/s)
Reading package lists... Done

E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/yakkety/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/yakkety-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/yakkety-backports/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/yakkety-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)

E: Some index files failed to download. They have been ignored, or old ones used instead.

ian@ian-Dell-DM061:~$ sudo apt-get upgrade

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Calculating upgrade... Done

0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

ian@ian-Dell-DM061:~$ 


```

Now if i try Software Updater, i get the same 'Failed to download repository information, Check your internet connection' again.....

Any help would be great thanks folks \\:D/

---

### Post by Frogs Hair on 2017-07-14
It could be the particular download mirror selected in software & updates. In the past I've found this to be temporary problem , so you may want to wait before selecting a different mirror.

---

### Post by MadMonkey1966 on 2017-07-14
Thanks Frogs Hair....that is very odd, i have been trying to do this for a few days now. Just tried again and now it has downloaded & installing lol

Many Thanks anyway.

---

### Post by ajgreeny on 2017-07-14
Don't forget that 16.10 will lose support very soon if it hasn't already, so you should update to 17.04.

Many users, including me, use only the LTS versions for their main installations so as to get the longer support, 5 or 3 years depending on the DE version you prefer, as opposed to 9 months for the intermediate versions.  The current LTS is 16.04, the next will be 18.04.

---

