---
title: "VLC plays movies locally but not over LAN"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Jannoth on 2006-11-01
Brand new installation of Ubuntu and VLC on very high spec PC (ie 1GB RAM, AMD64 3500 CPU, ATI PCIE Video etc).  This worked on XP but who wants Windows anymore??

On XP, I would browse the LAN to find a movie I liked on any other workstation then select and watch it (ie. without having to download it first) using VLC, BS Player - or whatever.

But, since loading Ubuntu, I have no choice but to copy the movie to the local machine before VLC will play it :

1. if I browse the LAN and double click on a movie, VLC pops up but doesn't play anything - just waits for something until I close it (wait 5 minutes or so);
2. VLC "File Open" dialog boxes only display local folders and desinations so I can't even browse the LAN with them.

Anyone reading this will have guessed that I'm only a week old baby/noob in terms of Linux, so please be gentle and kindly point me in the right direction.  I'm getting there :-)

Thank you in advance.

---

### Post by mgmiller on 2006-11-01
VLC does that.  It won't play over a lan.  The default movie player app (totem) will.  You don't say what OS the machines on your lan are.  If they are also Ubuntu, you would need to set up NFS to get vlc working.  It's a bit of a pain.  If they are not Ubuntu, just try opening them in Totem movie player.  If you have not installed all the codecs yet, try either easyubuntu: [http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/") 

or automatix:  [http://www.getautomatix.com/]("http://www.getautomatix.com/")  .  Cruise the forums for feedback on these 2 amazing apps before trying them, then decide which you want.  You only need one of them.  They both make installing everything very easy.

---

### Post by kkinder on 2006-11-01
There's a separate menu item to open a URL in VLC. Go to File -> Open Network Stream.

You may also give Totem a try.

---

### Post by sjnovick on 2006-11-01
In Ubuntu 6.06, VLC ***did*** play movies over the LAN.  It seems to be broken in 6.10.  I don't know if VLC has been "upgraded" or if something in Ubuntu 6.10 broke the feature in VLC.

MPlayer as well as Totem will play a video over a LAN nicely.

---

### Post by wrybread on 2006-12-02
> MPlayer as well as Totem will play a video over a LAN nicely.

Hmm, not for me they don't. Totem sits there buffering and never starts playback, and Mplayer doesn't even do that. I'm on Ubuntu 6.10, and yes I have the codecs (copying them locally plays fine).

Is there any clever way to get network playback of movies to work? This is a serious dealbreaker for Ubuntu for many people if not. In Windows this is trivial and mostly flawless, provided you're using a wired connection. And even if your connection has glitches you can use BSPLayer, which has a configurable network buffer.

---

### Post by robertpolson on 2007-01-16
The only solution I found is to mount the location you are trying to play from and then play the files from that folder.

---

### Post by WetWired on 2007-10-05
I am also having this problem. I USED to work. One of the updates broke it, which seems to be happening more frequently with Ubuntu.

---

### Post by Sifo77 on 2007-10-06
Same problem with ubuntu 7.04 feisty on my laptop, when i try to play up an .avi file on my MS server 2003. 

If i try to open the file with Movie Player i get an error message "An error occurred, Internal data flow error", if i try to open the file whit VLC the only thing that happens is that the VLC will popup thats it. And nothing happens if i try to open it with Mplayer.

I have googeld around for an solution and found diffrent solutions to the problem but non of them have worked for me.

I am new in linux, need step by step guide... Some one?

---

