---
title: "Gutsy installation pausing"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by Buickman on 2007-10-01
Intel Core 2 Duo E6600
Asus P5N32-E SLI Plus 
1 gig ddr2
1 80g sata II 
3ware 9650SE-4LPML - 4x seagate 320g in raid 10
NVidia 7300

I'm trying to do a clean install of gutsy (beta) amd64 with the alt-install cd. The installation itself is going on the 80g harddrive. Everything seems to be going fine. At one point a window pops up and asks if I want to d/l language packs. I've said yes and no during various attempts. It continues on until it gets to 85% (Installed Tomboy), then appears to freeze. I finally left it alone for about 30 minutes and it finished the install. When i got into gutsy, the network adapter wasn't working and was set to roam. I manually set it to static and entered the ip, subnet, gateway, etc, and still got nothing. Just for a test, I installed Feisty on this setup and had no issues whatsoever. Just wondering if anyone else has experienced this or maybe knows what's causing it.

Thanks

---

### Post by pay on 2007-10-01
Does it work if you upgrade from a feisty installation?

---

### Post by Buickman on 2007-10-01
I haven't tried that yet but I will when I get home from work. I was somewhat reluctant after seeing many posts about upgrade problems.

---

### Post by PmDematagoda on 2007-10-01
But that doesn't mean Gutsy is better, Gutsy has the new stuff, but it is also not as stable as Feisty since it still is in development, but it is going to be released soon.

---

### Post by gurkha on 2007-10-20
I just tried to install 7.10 64-bit with the alternate cd and experienced the same problem(Freezes at "Installed Tomboy" at 85%), except I aborted the install after waiting for 40 minutes, is it supposed to take this long? I'm downloading the live-cd version instead now, hoping the installation process will be shorter.

---

### Post by autonomouse on 2008-02-05
Guess I'm a little late in joining this conversation, but I had the same problem and have now found the cause and I wanted to redirect anyone else having this problem to this:

[http://psubuntu.com/forum/viewtopic.php?p=6869&sid=c5ba87893bf31a4af2a77be61cabace4](http://psubuntu.com/forum/viewtopic.php?p=6869&sid=c5ba87893bf31a4af2a77be61cabace4)

Basically, my problem was that I was downloading some huge file on another computer sharing the same internet connection. I know it seems obvious now, but I didn't even realise that it was trying to get onto the internet to download upgrades. Maybe it didn't say anything 'cos I was doing a text-based install? (my Samsung Q45 doesn't like the live CD install - something to do with the Intel graphics card...)

So, yeah, I just unplugged t'internet and it didn't pause - I'll download the upgrades at a later date.

---

