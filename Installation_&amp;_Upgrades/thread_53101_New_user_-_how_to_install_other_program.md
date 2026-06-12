---
title: "New user - how to install other program"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by ttwonder on 2005-07-30
Hi everyone,

I am a totally new user to Ubuntu and linux. I once tried to use Redhat LInux about 7 years ago not quite successful, basically due to hard ware problem and gave up. I decide to try it again with Ubuntu when I get a cover disk. I have install the latest H H version, but then don't know how to start. I have installed it on a Toshiba notebook Satellite 1800, however it is not connected to the Internet. I have another desktop that can connect to a dial up internet account and download.

I would like to play Divx video on the notebook. I can play it in Win Xp or ME with Xvid but don't like how to play it with LIinux. Tofem told me additional plug in required. But how to do that? I have gone through the Ubuntu site and other sites of Xvid without much hint. HELP!

Sorry to ask such a silly question, but the Linux book I bought only talks about RPM package which is not supported in Ubuntu. What is the easiest to install drivers, programs? (IS it as easy as Windows?)

Thanks a lot.

ttwonder.

---

### Post by slada on 2005-07-30
Welcome!  I am slowly being converted to Linux myself.  Ubuntu is the best distro I have found so far to help me make the jump.

The answer to your question can be found here:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

In short, you want to open a terminal (Applications/System Tools/Terminal) and type the line:

sudo apt-get install libdivx4linux


I recommend exploring ubuntuguide.org for more help in getting started with Ubuntu.

---

### Post by pabc on 2005-07-30
Hi,

the first thing to do is get extra repositrys onto your system so apt-get or synaptic (nice graphical front end to apt-get) can get the extra software easily which didnt come with the standard CD

read this [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) for a very simple way of doing it.

Once you've got that done open synaptic package manager (main menu > system > administration)

Taking your divx playback problem as an example, "search" for divx, wait a few secs and all the packages related to divx appear. Hightlight each one for a description. as you'll see libdivx4linux is there. right click and "mark for install" then click apply. 

The package downloads and installs. when its done you'll be able to play divx movies.

Have a read through  [http://ubuntuguide.org/](http://ubuntuguide.org/) as it spells out all the other bits and bobs you'll most likely need to install.

P

---

### Post by JaS on 2005-09-25
[QUOTE=pabc]Hi,

the first thing to do is get extra repositrys onto your system so apt-get or synaptic (nice graphical front end to apt-get) can get the extra software easily which didnt come with the standard CD

read this [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) for a very simple way of doing it.

Once you've got that done open synaptic package manager (main menu > system > administration)

Taking your divx playback problem as an example, "search" for divx, wait a few secs and all the packages related to divx appear. Hightlight each one for a description. as you'll see libdivx4linux is there. right click and "mark for install" then click apply. 

The package downloads and installs. when its done you'll be able to play divx movies.

Have a read through  [http://ubuntuguide.org/](http://ubuntuguide.org/) as it spells out all the other bits and bobs you'll most likely need to install.

P[/QUOTE]

Thanks for the info thats a great guide to get Ubuntu running ... everything just how you want it.I just got my cd's in the mail afew days ago and decided to give Ubuntu a try.With that guide i can really enjoy this O/S.

---

