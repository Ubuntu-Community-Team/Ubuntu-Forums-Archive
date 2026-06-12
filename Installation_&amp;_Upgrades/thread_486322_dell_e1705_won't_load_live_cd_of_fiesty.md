---
title: "dell e1705 won't load live cd of fiesty"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by l33t_tj on 2007-06-27
I wanted to dual boot vista and ubuntu, but the live cd won't boot.

It stops after "running local boot scripts" and it says "bcm43xx error microcode "bcm43xx_microcode5.fw" not availible or load found"

need help... :(

---

### Post by kaltv on 2007-06-28
Are you sure the livecd is correct? Did you order it or burn it yourself?

I've had hell burning the livecd myself at first. No matter how many times I downloaded, the md5sum wouldn't match. 

Then I downloaded via bittorrent and that solved the problem (apparently bittorrent checks for the integrity of the file as it goes).

Then it took me several burns to get a correct one (I had to use a better quality CD than the ones I tried at first).

After that, once you've loaded the menu, you have to do a CD integrity check (to make sure you don't have to do yet another burn... again).

The installation help guide is here:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

There are more detailed sections on how to check the integrity of the CD.

From there maybe you can tell us where exactly the problem started; download level (if you burned the CD yourself), disc-burning level, or something else.

---

### Post by l33t_tj on 2007-06-28
The disc is an official one of my friends.  He has installed it succesfully on 2 other machines and they work fine.

it tries to boot the live cd but doesn't get past the broadcom bcm43xx driver giving the error message i said in my last post.

my laptop is an e1705, if i didn't already say that, it is late

---

### Post by kaltv on 2007-06-28
Okay, so it isn't a CD integrity problem.

Strange, the errors you've mentioned seem to have to do with wireless connection. But, while it would make you unable to access a network, it should Not have outright prevented the installation. :( 

It shouldn't be a hardware incompatibility either. This guy for example managed to install Edgy Eft:

[http://zapek.com/?p=7](http://zapek.com/?p=7)

I'm sorry, I have no idea why it would prevent installation completely. :( Hopefully someone else will have a better idea.

---

### Post by l33t_tj on 2007-06-29
It has something to do w/ the broadcom 43xx wifi card, dave probably has the intel one.

---

