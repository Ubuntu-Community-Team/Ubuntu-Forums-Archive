---
title: "ubuntu 10.04 problem installing libncurses5-dev"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by niki+a on 2011-01-02
Hi,

I am trying to install the libncurses5-dev package via

sudo apt-get install libncurses5-dev

and it does this

```

(Reading database ... 
dpkg: warning: files list file for package `libncurses5-dev' missing, assuming package has no files currently installed.
(Reading database ... 246291 files and directories currently installed.)
Preparing to replace libncurses5-dev 5.7+20090803-2ubuntu3 (using .../libncurses5-dev_5.7+20090803-2ubuntu3_amd64.deb) ...
Unpacking replacement libncurses5-dev ...

```

and then it hangs... it's been sitting at that point for about 24 hours. 

So I killed the process and no matter what I try to install I guess dpkg has to fix the above problem first by re-installing it from repository and it... hangs. 

So now I cannot remove it and I cannot install anything else and it's very frustrating.

What can I do to remedy this problem?

I'm running Ubuntu 10.04 64 bit:

Linux ubuntu 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

---

### Post by lithopsian on 2011-01-02
First try:
dpkg --configure -a

This might fix your repository.  If not, reboot and check your drives for any corruptions, then try again.

---

### Post by niki+a on 2011-01-02
> **lithopsian said:**
> First try:
dpkg --configure -a

This might fix your repository.  If not, reboot and check your drives for any corruptions, then try again.

Hey, I did all that. I know my way around dpkg enough to run that command and rm locks... 

I actually did some digging and ran some other commands like:

sudo dpkg --remove --force-remove-reinstreq libncurses5-dev

That fixed my repo and I physically removed all files related to that package. So as far as apt is concerned it's a *done deal* (fixed). However, new problem --- seems apt just hangs.

So I'm thinking nothing is wrong with package but rather apt is f-ed up. I try to install other software and it just hangs as soon as it start unpacking... should I re-install apt? It's weird as **** man... I swear these things only happen to me. I'm like the guy in Douglass Adams novels.

---

### Post by niki+a on 2011-01-02
Weirdest thing...

I restarted my computer and ran the same commands using 

```
sudo aptitude install <package name>
```

and everything worked fine. 

Note I used:

```

sudo dpkg --configure -a

sudo rm /var/cache/apt/archives/lock

sudo rm <other locks>

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

sudo dpkg --remove --force-remove-reinstreq <package name>
```

(All to no avail prior to sys restart.)

I don't know, as much as I like linux, ideas behind it and general nature of it, regretfully, even as of 2010, it's not quite ready for prime-time as a viable desktop solution. 

I mean, if I wasn't a programmer I doubt I would have walked away with anything but frustration from this expirience.

---

