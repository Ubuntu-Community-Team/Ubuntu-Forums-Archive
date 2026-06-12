---
title: "sound problem"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by nuke_fluke on 2008-04-27
I upgraded Gutsy Gibbon to Hardy Heron but the sound quality is very poor and harsh..
is there any problem with audio driver??

Please help...

---

### Post by teknomatrix on 2008-04-28
Well I have the same problem as well .. ALSA worked gr8 with my Gibbon (7.1) and after upgrading everything is fine except the sound ... 
it does work .. but its gross .. not normal .. its harsh and I dont know how to describe the sound that comes out .. lolz

any fixes yet ?

---

### Post by Sub101 on 2008-04-28
I've got the same problem. As far as I can see this is the first thread to mention it?

---

### Post by Sub101 on 2008-04-28
[http://ubuntuforums.org/showthread.php?t=737414](http://ubuntuforums.org/showthread.php?t=737414)

this worked for me

---

### Post by teknomatrix on 2008-04-28
Well I checked several places .. and the following worked for me :

[http://www.alsa-project.org/~jfulmer/alsa-faq.html](http://www.alsa-project.org/~jfulmer/alsa-faq.html)

Refer section 2.8

or 

just reconfigure PCM level in AlsaMixer. By default on installation it was set to 635 way over the max limit of 100. I guess that was causing the sound to distort. As soon as I got it within 100, everything was fine. 

:)

---

### Post by LeslieL on 2008-04-28
Thanks for reminding me of alsamixer. I was wondering why I didn't have any sound. Checked alsamixer: the pcm level was set at 0. The most useful question, I find, when troubleshooting is "Is it turned on?" Trouble is, I keep forgetting to ask it.

---

### Post by nuke_fluke on 2008-04-28
Thanks...will inform as soon as I check it out..

---

### Post by nuke_fluke on 2008-04-29
problem solved....:guitar::)

thanks once again...

---

