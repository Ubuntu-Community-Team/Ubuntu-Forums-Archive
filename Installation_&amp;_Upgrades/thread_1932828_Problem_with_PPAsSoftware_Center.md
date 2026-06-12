---
title: "Problem with PPAs/Software Center"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by Fkemble on 2012-02-28
Have used Ubuntu for the greater part of a year now at home, but still learning about dealing with issues(never really had one til now)-I was trying to add Songbird through terminal a few days ago (which I eventually was able to find a sudo apt that worked, although I tried a lot of things to get it installed). And I didn't notice this at first, but a little later I went into software center to add another program and the icon just kept turning, wouldn't load any software, won't let me view get software or installed software, just keeps turning. so I went into sources and removed all the extra ppa's like google, etc. Still the same. So I went package manager and this box popped up:

E: Type '“deb' is not known on line 1 in source list /etc/apt/sources.list.d/getdeb.list E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I learned so much when I used Windows b/c Windows always had problems and I've never ran into something in Ubuntu cause it just works and I honestly just don't know. I read up on going back to default repositorys..tried to reinstall software center with sudo apt and no luck. Can't find any mention at all of .deb files in repository. Tried to send a problem report under help in software center and I get an error for that. The box I pasted up there also comes up now when I go to update manager. In the repository list, right now, there's canonical and community maintained software checked - nothing under other-and only 2 under authenication ..and I just don't know really know deep linux to understand how to fix it, so a basic layout of how to go about it would be great.
Oh, and this was actually a fresh install that's only a few days old too and it was working fine til' I tried several sudo's trying to install songbird. My wife hates when I wipe the drive and go from scratch so I hate to do it twice within a week. Hoping someone has run into this before. Thank you.

---

### Post by plucky on 2012-02-28
> E: Type '“deb' is not known on line 1 in source list /etc/apt/sources.list.d/getdeb.list E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


The file is in **/etc/apt/sources.list.d**

Open a terminal and post output of ```
cat /etc/apt/sources.list.d/getdeb.list
``` or delete the getdeb.list file in **/etc/apt/sources.list.d**.


Good Luck

---

