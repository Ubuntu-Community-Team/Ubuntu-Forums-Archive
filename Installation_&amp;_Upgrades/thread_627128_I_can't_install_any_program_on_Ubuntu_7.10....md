---
title: "I can't install any program on Ubuntu 7.10..."
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by jpmelos on 2007-11-29
I can't install anything on my Ubuntu 7.10, anything I try to install, doesn't matter if it's by Synaptic, package or whatever, is denied accusing that missing libraries cannot be installed (as Synaptic tries to install all libraries missing for the program).

For example, I'm trying to install MPlayer by Synaptic, but all I get is:

```
mplayer:
 Depende: libartsc0 (>=1.5.0-1) but it is not installable
 Depende: libaudio2  but it is not installable
 Depende: libmad0 (>=0.15.1b) but it is not installable
 Depende: libmpcdec3  but it is not installable
 Depende: libpulse0  but it is not installable
 Depende: libungif4g (>=4.1.4) but it is not installable
 Depende: libxvmc1  but it is not installable
```

Any help is more than welcome, as I'm already considering going back to Ubuntu 7.04, because I could install anything there with a couple clicks...

---

### Post by Pumalite on 2007-11-29
Do all the updates due first and try again.
(I just installed Mplayer just to check and I had no problems. So, the problem is at your end.)

---

### Post by jpmelos on 2007-11-29
Hmm... I never upgraded my Ubuntu, because always when I ask the manager to check for updates, it says no upgrades were released after the launch yet. :O

---

### Post by Pumalite on 2007-11-29
Go to Synaptic, reload and mark all packages for upgrade.

---

### Post by jpmelos on 2007-11-29
Nothing happens at all.

---

### Post by oldos2er on 2007-11-29
Are all your repositories enabled?

---

### Post by jpmelos on 2007-11-29
Woah! I guess I was missing that, man. :D

Thanks a lot. I'll install all my stuff and report back here if everything was good or not. Thanks a lot! :D

Loads of upgrades to do now on Ubuntu, by the way. Haha!

---

### Post by erfahren on 2007-11-29
if there's not an internet connection present when installing Gutsy the repos will be commented out in /etc/apt/sources.list

That seems to be a new thing and I've seen it confuse quite a few people.

---

### Post by jpmelos on 2007-11-30
Yea, I guess that's what happened, because I was not connected to the Internet when I installed Ubuntu, and it warned it couldn't update. Then I rebooted to HD already and tried to update and said no update have been released. Now I enabled all repositories and downloaded 126 updates. :D

All problems solved. Thanks, people. :D

---

### Post by Pumalite on 2007-11-30
Good luck.

---

