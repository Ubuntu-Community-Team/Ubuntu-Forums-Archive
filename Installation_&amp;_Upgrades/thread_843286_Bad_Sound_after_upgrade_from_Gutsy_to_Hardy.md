---
title: "Bad Sound after upgrade from Gutsy to Hardy"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Herbert55 on 2008-06-28
Hi folks,

I am desperate about the following problem and your help is strongly appreciated. I updated a Thinkpad R61e from Gutsy to Hardy and now the sound is very bad. I know that there have been issues with sound in Hardy that are dealt with in this forum but this seems to be a different type of problem. I do have sound but it is very very bad. Problem appears with both ubuntu system sounds and music players. 
I am not very good in terminals, so I would very much appreciate if you could tell me the different steps that I need to follow to get this problem out of the way. 

Your help is GREATLY appreciated.

Best wishes,

Herbert

---

### Post by Pumalite on 2008-06-28
First of all do a full update of your new Hardy. Open up all your repositories, except src.
System>Administration>Software Sources>Click on proposed, updates, partner and backports. Then:reload
sudo apt-get update 
sudo apt-get dist-upgrade
Check your sound after a reboot and report back.

---

### Post by Herbert55 on 2008-06-28
First of all: Thank you for your help!

I followed all your suggestions but unfortunately there is no change.

Thanks anyways!

---

### Post by Pumalite on 2008-06-28
Post:
lshw -C sound

---

### Post by Herbert55 on 2008-06-28
Solved through 
sudo /etc/init.d/alsa-utils reset 
following an example from 
[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

Thanks a lot for your kind help!

Best wishes, 

Herbert

---

### Post by Pumalite on 2008-06-28
You are welcome. Good luck!

---

