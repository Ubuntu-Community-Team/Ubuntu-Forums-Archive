---
title: "Can't upgrade from jaunty?"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Ubumanda on 2011-04-29
I'm on 9.04 and decided to upgrade to 10.04 LTS, by upgrading 9.04->9.10 and 9.10->10.04.  However, I'm stuck in the first step because my installation doesn't see anything to upgrade to:

abf@niterinep:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
abf@niterinep:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

This is after I tried: 

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get clean
sudo apt-get update

I do have a USB stick with which I can do a clean install of 10.04 LTS, but for fun and education I want to do it the messy way first.  So what could be causing this?  Should I post my /etc/apt/sources.list?

---

### Post by Ubumanda on 2011-04-29
Got it!  I had to change Prompt=never in /etc/update-manager/release-upgrades to Prompt=normal, and voila, it works.  I must have turned prompts off in upgrade-manager way back when.

(Now how do I change the thread prefix to [SOLVED]?)

---

