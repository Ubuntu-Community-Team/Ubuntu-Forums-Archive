---
title: "New ubuntu user"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Mr1102 on 2010-10-14
Hi, My name is Nathan. My friend got me to put ubuntu 10.10 on my new laptop.

I kinda like it so far but I'm really having trouble with alot of things and it's starting to annoy me.

my last os was xp, I was about to jump to w7 but like a said a friend want's me to try this 10.10.

I'm having trouble installing and running just about everything. 1st it was drivers, like cheese for my wc.
It downloads but wont install because the archive manager can't read it or something. I tryed to get arc on it and I get the same problem.

it won't read any of my software cds like DVD suite, or downloads like mabinogi.

I feel like such a stupid noob cuz I'v got no idea how to fix any of this.

plz help, I'd rather not go back to windows but I'm really getting close as these problems are becoming really annoying.

---

### Post by night_fox on 2010-10-14
You can't install Windows programs on Ubuntu. You have 4 ways of getting around this:

1) Find an alternative program for linux (Free)
2) Use WINE to run windows programs on linux
3) Use a virtual machine to run windows from within linux
4) revert to windows

Do you have any more specific problems?

---

### Post by nerdy_kid on 2010-10-14
one thing that I didn't realize when I first started ubuntu is that there was 30,000 programs sitting in the software channels.  The add/remove software program in your "applications" menu should have most all the software you need.  If you are looking for an alternative to windows software then post a thread asking about it -- there is probably one.  You *can* run windows programs in Ubuntu BUT there is a very large chance that they won't work right/as well as they do under windows so you should try and look for alternatives instead.

Ubuntu won't play dvds by default due to legal reasons, open a terminal and run

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

it will ask for your password -- you won't be able to see your password as you type it -- this is normal.


Give Ubuntu at least a month to get used to everything, and if you cant stand it then switch back to windows.
I used to be a huge MS fan (yes it is true...) now look at my sig :D  Once I got switched from windows...I dont know how I lived without Linux :D  I use exclusively Linux now, have a Win XP vm that I boot about once a month for about 20mins.

---

### Post by Mr1102 on 2010-10-15
ya, my windows 7 cd came in the mail just yesterday, now im Dbooting it with ubuntu.

After getting it working I did updates on ubu to get must of the freeware drivers i'd need. then my nvidia card apparently needed a proprietary driver, so I installed it.

after installing I rebooted and when ubu tries to start up it gets to "checking state of battery" and just sits there. should I reinstall ubu to fix this, or is there something else

ps: try for the DVD info. I was wondering about that xD

I don't know much about ubu, I'v only just started using it for about 2 days now.

all I know is how to find freeware, little bit of how to partition it. customizing, and ipconfig = ifconfig, and a few other miner things.

anyways I'll probably refer to these forums for most of my problems till I get to know this os better, so any help is appreciated.

I feel like I'm forgetting something....O well

---

### Post by Mr1102 on 2010-10-15
Oh yeah!
now I remember I plan on using Vmachine on both ubu and w7, so I can run either on whichever. I think that should solve most of my software issues.

---

