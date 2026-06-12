---
title: "How to Install Creative Drivers. Sound Problems"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by Jalh on 2008-06-12
Hey guys first at all im a newbie in linux world. My first impression was great with ubuntu and im happy with it. Here is my problem, i own a "Creative Sound Blaster X-Fi Elite Pro", i have downloaded the drivers that they recommend ( Creative ) from they website. I dont know to install them and i don't have sound ( obliviously ). I would like to use linux as my fist operative system and use xp for gaming. Any help will be thanked. 
greetings !

---

### Post by Jalh on 2008-06-12
any help ?

---

### Post by Partyboi2 on 2008-06-12
Open a terminal (Applications>Accessories>Terminal) and change directory to where the downloaded file is, so if its on your desktop type
```
cd Desktop
```then extract it
```
tar xvzf XFiDrv_Linux_US-1.18.tar.gz
```then change into the newly created directory
```
cd XFiDrv_Linux_US-1.18
```then run the installer
```
sudo ./installer
```
[[COLOR=Blue]Here[/COLOR]]("http://ohioloco.ubuntuforums.org/showthread.php?t=571656") is a thread that deals with xfi beta driver

---

### Post by Jalh on 2008-06-12
thanks for your answer !

---

### Post by CarnageHeart on 2008-07-18
Ahh Google works wonders, I thank you for the help too, however... I have a small problem with the installation. Heres what happens (screen shot included)

[IMG]http://members.cox.net/shurakokoro/error.jpg[/IMG]

I'm new to the world of Linux as well, and any help is much appreciated. If you need any additional information please let me know.

---

### Post by evets25 on 2008-07-18
Yeah, those x-fi "drivers" are only beta, and barely functional and a pain in the a$$ to install and get working. Practically speaking, there are no functional X-fi drivers. Bottom line: you need to go buy a sound card that works under linux. If you're not happy with this, let creative know, and maybe someday they'll start listening and actually release some working drivers... 

Also, this would be a good time to point out that *none* of the sound cards that are currently listed for sale on the creative website have working linux drivers yet, except SB live! - extrenal, and the audigy SE, but even that one has a crappy driver that won't do hardware mixing! :( I know, because I have it...

But I'm not bitter... oh no...

---

### Post by CarnageHeart on 2008-07-18
> **evets25 said:**
> But I'm not bitter... oh no...

Not quite so subtle sarcasm ftw! XD

Yeah, I know they're beta drivers.. but I was kinda hoping to at least get a "bing" or something ya know? Or even a generic driver that can just get sound working without the extra features. No such luck though I guess :(

---

### Post by CarnageHeart on 2008-07-18
> **Partyboi2 said:**
> 
[[COLOR=Blue]Here[/COLOR]]("http://ohioloco.ubuntuforums.org/showthread.php?t=571656") is a thread that deals with xfi beta driver

Just noticed that and used it, worked perfectly. THANK YOU! =D

---

### Post by go_beep_yourself on 2008-10-08
> **evets25 said:**
> Yeah, those x-fi "drivers" are only beta, and barely functional and a pain in the a$$ to install and get working. Practically speaking, there are no functional X-fi drivers. Bottom line: you need to go buy a sound card that works under linux. If you're not happy with this, let creative know, and maybe someday they'll start listening and actually release some working drivers... 

Would you like to sign an online petition to get Creative to release Linux sound drivers? Think if enough people sign it, it may get there attention.

---

