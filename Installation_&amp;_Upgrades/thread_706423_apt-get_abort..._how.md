---
title: "apt-get abort... how???"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by xanas3712 on 2008-02-24
I was trying to install kdegames-kde4 but now I get a bunch of lame errors.  I can't abort, continue, or do anything.  dpkg -a --configure doesn't work and I can't find a post on how to abort or continue, so I guess somehow it's a problem only I have had.

Common questions:
1) No I don't have any prior kde4 packages
2) Yes I'd like to have the programs installed if possible
3) Error message?

Unpacking libkdegames4-kde4 (from .../libkdegames4-kde4_4%3a4.0.1-0ubuntu1~gutsy1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libkdegames4-kde4_4%3a4.0.1-0ubuntu1~gutsy1~ppa1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/libkggzgames.so.4.0.0', which is also in package kde4games

I have read there is a way to force overwrite of already installed file, but why does this stupid error even exist and why does the package want to do something inane like that....  Besides that I can't figure out how to actually force the overwrite, and I get that message for 50 different packages so it'd kinda be a pain to have to do this with all of them.

ugh..

I was able to force removal with the "easy" to use aptitude dpkg recommended using.. but I'd like to know what the proper commandline is as that program is oddly setup.  And since I'd actually like to install the packages.. (which I somehow managed to do on another system here).. I'd really like to know how to resolve instead of just purging the packages.

---

### Post by xanas3712 on 2008-02-24
Annoying, but was able to resolve myself, turned out the option in apt I had selected was pulling in conflicting packages kde4games and kdegames-kde4

I removed kde4games and kde4games-data and was able to proceed with kdegames-kde4

---

