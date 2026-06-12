---
title: "Need some help w/ ati drivers"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by dfnkt on 2007-02-06
I'm new to linux, currently have ubuntu 6.10 edgy installed. Must say first off that i am enjoying it. Ok heres my questions, I am looking to run a Warsow server with this machine, for anyone unfamiliar with warsow [www.warsow.net](www.warsow.net) 

When I launch the game it stops because it couldnt load the openal sound module, i was wondering how to install this sound module (driver maybe?). I have downloaded openal-0.0.8-1.i586.rpm. How do I install this file, and what to linux is an RPM file?

Also I am running a radeon 9200 with 64MB ram, wondering how do install the driver for it, i found a guide on the net and followed the various commands, got all the way through it and got stuck where it said i needed to type in "sudo aticonfig -initial" it gave an error saying i needed to copy the config file to /etc/X11

Can someone help the new guy please? Thank you so much in advance

---

### Post by taurus on 2007-02-06
Maybe this guide would help with your ATI graphic card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by dfnkt on 2007-02-06
I think i got the ATI driver installed, what about getting sound? My PC is an Abit BE7-G with onboard says "AC97" on specs, and their site lists realtek drivers. have a celeron 2.4 w/ 512MB ram.

---

### Post by voltsy on 2007-03-12
hi dfntk,

if it's any consolation i've also been trying to get openAL to work on Dapper Drake, without success, to date. I think the people who removed the code from an earlier version of ubuntu might have made a bad judgement. They thought it was used only for skyrocket screensaver, but the gamers seem to have use of it as well. 

Maybe if we got down and dirty under the hood, and learned how to compile modules, we could reinstate openAL as a loadable module (??) - that is presently beyond my skill level :-(

If somebody has done that, please outline your procedure here (thanks!!)

---

### Post by voltsy on 2007-03-12
openAL seems to be near death as a web-based entity.

However! although [www.openal.org](www.openal.org) and opensource.creative.com are both offline at present you might be able to get some good info accessing pages through Google caches:

[http://www.google.com.au/search?hl=en&q=openal+site%3Aopensource.creative.com&btnG=Search&meta=](http://www.google.com.au/search?hl=en&q=openal+site%3Aopensource.creative.com&btnG=Search&meta=)

.... the "[Openal] openal on linux" is useful, but don't click directly on it, click on the "cached" link to view the cached version. Since ubuntu is a child of Debian, I hope the info is relevant. (no guarantees, I have not succeded with openal yet)

More stuff here (again follow only Google's "cached" links):

[http://www.google.com.au/search?hl=en&q=site%3Awww.openal.org&btnG=Search&meta=](http://www.google.com.au/search?hl=en&q=site%3Awww.openal.org&btnG=Search&meta=)

come back soon, [www.openal.org](www.openal.org), all is forgiven!!

---

