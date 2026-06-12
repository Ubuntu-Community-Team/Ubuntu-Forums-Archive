---
title: "[SOLVED] For Feisty / 7.04 -- Default sources.list?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Phrawm48 on 2008-04-28
Can someone please tell me how I can "reset" my Feisty / 7.04 *sources.list *to its default, baseline state?

I can't believe this information is evidently so difficult to obtain, but both a Forum Search and a Web search haven't provided me with a simple list of the default repos.

I tried using Synaptic's "Select Best Server" feature to try and cirumvent the network blockages that seem to have resulted from the recent releast of Hardy / 8.04.  This seems to have screwed things up so badly that all I want to do now is just get back to the as-installed state...

Cheers & thanks,
Ric
SFO

---

### Post by overdrank on 2008-04-28
> **Phrawm48 said:**
> Can someone please tell me how I can "reset" my Feisty / 7.04 *sources.list *to its default, baseline state?

I can't believe this information is evidently so difficult to obtain, but both a Forum Search and a Web search haven't provided me with a simple list of the default repos.

I tried using Synaptic's "Select Best Server" feature to try and cirumvent the network blockages that seem to have resulted from the recent releast of Hardy / 8.04.  This seems to have screwed things up so badly that all I want to do now is just get back to the as-installed state...

Cheers & thanks,
Ric
SFO

Hi and 
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free 
```
Found here
[http://www.psychocats.net/ubuntu/sources#feisty](http://www.psychocats.net/ubuntu/sources#feisty)

---

### Post by Phrawm48 on 2008-04-29
OD:  Thanks! for your help with this.  Cheers, RB

---

