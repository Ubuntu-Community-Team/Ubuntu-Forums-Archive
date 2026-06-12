---
title: "finding ppa's??"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2013-12-13
Hi all,

I recently discovered that I can use an existing (and properly operating) linux partition to clone an exact copy of itself in another partition. This makes fresh installs lightning fast and doesn't download any data or involve a slow installation process.

My question is about ppa's. I found most of the information I needed about ppas, except for one issue.

I am developing a list of terminal commands that installs and sets up a fresh install just the way I like. I now install software in terminal, with a single cut and paste. However, software installed in this manner doesn't add a ppa, so improvements and newer versions are not downloaded automatically. 

I find many programs have no ppa listed however. Do I need to look harder for a ppa for a particular software package, or is it normal for some software to have no ppa associated with it??? If I can't find a ppa for a program at [http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas), can I assume there is no ppa.....or are there other sources of ppa listings???

TIA, and GO LINUX!!!

Art

---

### Post by Bucky Ball on 2013-12-13
If it's in the repositories it will get updates and is in the Ubuntu PPA already. Because you're using a terminal makes no diff. Synaptic and Software Centre are front-ends for apt-get basically so you're doing the same thing. 

If it's in the repos it will get updated with the regular system updates.

Generally, it's things that aren't in the repos that need manually installed PPAs so they will get updated, as you are finding out. It's kind of the luck of the draw. Some apps have a PPA, others don't. Is there anything that you are installing via the terminal that is not in the Ubuntu repos or not a PPA? Whatever falls into that category are the only ones you need to worry about updating manually or finding a PPA or waiting for the day it becomes part of the Ubuntu repos.

---

