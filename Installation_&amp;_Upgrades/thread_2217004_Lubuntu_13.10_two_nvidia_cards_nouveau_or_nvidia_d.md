---
title: "Lubuntu 13.10 two nvidia cards nouveau or nvidia driver"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by jonytrifulca on 2014-04-15
Hi guys
 Recent install Lubuntu 13.10, I want have extended Desktop, two monitors with nvidia or nouveau drivers. I have two nvidia cards one output by each. Nvidia GeForce 6150SE nforce430, and nvidia Geforce G210. First I try with nouveau drivers and arandr but I always have a black active monitor:

[IMG]http://i62.tinypic.com/65swgi.png[/IMG]

Is curious, I take a print pant and I can see two desktop, but one of them is active(power on, green light), but back, on startup its show lubuntu design:

[IMG]http://i62.tinypic.com/ngqetf.png[/IMG]


And I can't install nvidia drivers because when I install one, the installation remove the other::(:
I try nvidia-319 for GeForce 6150SE , and nvidia-173 for Geforce210

[IMG]http://i60.tinypic.com/t0qiv8.png[/IMG]

Some ideas??
Any help is appreciated!!
Thanks!

---

### Post by jonytrifulca on 2014-04-16
Some ideas? Experiences?
Any clue is appreciated, thanks for share

---

### Post by jonytrifulca on 2014-04-16
Ok, resolved, was a problem with nvidia driver and kernel 3.11, you must patch the .run file 
[http://www.linuxquestions.org/questions/slackware-14/nvidia-304-xx-4175458722/page3.html](http://www.linuxquestions.org/questions/slackware-14/nvidia-304-xx-4175458722/page3.html)

I patch the 304.108.run for Geforce 6150SE and now work all ok, two monitors with nvidia-settings and xinerama

Thanks!

---

