---
title: "vlc problem"
date: 2015-04-19
forum: Installation &amp; Upgrades
---

### Post by seiifboyka on 2015-04-19
plz help me guys when i type **sudo apt-get install vlc** i get this message (i have ubuntu 14.04 by the way)
[B]    Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 3.0.0~~git20150319+r59816+33~ubuntu14.04.1) but it is not going to be installed
       Depends: libavcodec55 (>= 6:9.1-1) but it is not installable or
                libavcodec-extra-55 (>= 6:10~~git20131218.b3189af~ubuntu14.04.1) but it is not installable
       Depends: libavutil53 (>= 6:9.1-1) but it is not installable
       Recommends: vlc-plugin-notify (= 3.0.0~~git20150319+r59816+33~ubuntu14.04.1) but it is not going to be installed
       Recommends: vlc-plugin-samba (= 3.0.0~~git20150319+r59816+33~ubuntu14.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.    [/B]

---

### Post by mc4man on 2015-04-19
You are trying to use the vlc build from the videolan master ppa [https://launchpad.net/~videolan/+archive/ubuntu/master-daily](https://launchpad.net/~videolan/+archive/ubuntu/master-daily)
The ppa depends on other ppa's to produce the trusty builds & that makes it basically worthless for trusty users.
(- not to mention it has stopped building, at least for now.

Specifically it's using a ppa that has libav10 (ie. libavcodec55, ect.), that's why you can't install as by default trusty uses libav9, (libavcodec54, ect). So as far as 14.04 the ppa is a joke, get rid of it..
(- you could add the ppa(s) it deps on though no assurance it won't cause you issues so I won't provide links.

---

### Post by seiifboyka on 2015-04-19
how exactly can i fix it  ?
i am sorry but i am new on ubuntu 
and thnx

---

### Post by mc4man on 2015-04-19
Do you remember adding the ppa?

---

### Post by seiifboyka on 2015-04-19
hhh yes i deleted them and it worked thanx 
u really helped alot

---

### Post by mörgæs on 2015-04-19
If the problem is solved please mark the thread so.

---

