---
title: "Real player uninstall"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by mavenuparker on 2009-12-10
I've installed Real Player 11  by....

 wget [http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin)

chmod a+x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

There is no sound output so i tried to uninstall it using(Followed a forum....Im an absolute beginner)

sudo dpkg -r realplayer

it returned

dpkg - warning: ignoring request to remove realplayer, only the config
 files of which are on the system.  Use --purge to remove them too.

sudo dpkg -r realplay 11.0.1.1056 

dpkg - warning: ignoring request to remove realplay which isn't installed.
dpkg - warning: ignoring request to remove 11.0.1.1056 which isn't installed.


locate realplay

/home/lakshmi/.config/real/realplayerrc
/var/cache/apt/archives/realplayer_11.0.0-0.2medibuntu2_i386.deb
/var/lib/dpkg/info/realplayer.list
/var/lib/dpkg/info/realplayer.postrm

i tried removing them using

sudo rm -f /var/lib/dpkg/info/realplayer.list
sudo rm -f /var/lib/dpkg/info/realplayer.postrm

but that did not give any reply....
i still have the real player in Applications-->Sound and video--> Real Player 11
now...when i try to play a media file it simply crashes down....

Please help me uninstall it....

---

### Post by mavenuparker on 2009-12-11
How to reinstall it??

---

### Post by SlugSlug on 2009-12-11
> **mavenuparker said:**
> How to reinstall it??

search in symantic package manager 

system > addmin > synmantic

---

### Post by oldos2er on 2009-12-11
I think you'd run the script /opt/real/RealPlayer/postinst/postuninst.sh , assuming you chose the defaults when you installed it.

---

