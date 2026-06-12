---
title: "Upgrading from 10.10 to 11.04, back to login with install process still in background"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by zeflash on 2011-07-27
Hi, I'm still fairly new to linux so this might seem like a stupid question, but given I'm stuck and haven't been able to find anything to help on the net, I'm posting out for help here.

I've had a 10.10 installed for a while, and today I figured I'd do the proposed upgrade to 11.04. A first time for me.

The process was going along fine, and at some point it asked me what to do about a conf file that was changed by both me & the update. After looking at the diff, I figured I'd edit the file myself. So I told it I wanted a prompt, I started emacs on the file..

and after the ctrl-x ctrl-c I ended up with a busted prompt that wouldn't display the CR properly. Given I read I had to exit after I was done, I typed exit, and went back to the login prompt!

Now that I'm logged back in, I can see the upgrade process still waiting to do something:
 2472 ?        S      0:09 /usr/bin/python /tmp/update-manager-EbXeab/natty --mode=server --frontend=DistUpgradeViewText
  782 pts/0    Ss     0:00  \_ /usr/bin/dpkg --force-overwrite --status-fd 27 --configure libc-dev-bin linux-libc-dev li
20310 pts/0    S      0:00      \_ /bin/bash -i
20337 pts/0    S+     0:00          \_ emacs /etc/ppp/options

but I can't figure out what to do to "go back in". Am I hosed?

---

### Post by zeflash on 2011-07-27
Well in the end I tried to use reptyr which kinda showed me what was queried but I couldn't select any option. And after that it seemed to kill the process. Which enabled dpkg to continue.

I'm apparently properly upgraded now. Next time I'll use screen.

---

