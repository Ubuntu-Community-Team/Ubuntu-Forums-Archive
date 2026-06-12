---
title: "no sound in flash after updates"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by finley on 2010-07-29
Alright, so this is a long winded problem, but I'm sure it will be interesting to someone out there:
It all started when I updated to Firefox 3.6.8. At this point I was back in the stone age with Ubuntu 9.04. After the update, sound stopped working in embedded flash such as youtube. However, it continued to work in Epiphany. I decided that perhaps this was a problem that could be solved by updating to Koala. After doing so, sound stopped working in Epiphany as well (Video was still completely possible). Koala seemed kind of sketchy to me, to be honest, so I thought "why not just continue to the newest?". After updating to Lucid, I still had no sound. At this point I started a long serious of deleting and reinstalling Adobe Flash.
I believe that the first problem was that I had Flash 9 saved to my desktop and Firefox was trying to read that over Flash 10 or something. So, delete delete and all I have left is Flash 10 and in about:plugins that's what Firefox registers (specifically, I downloaded Flash 10 from the website and saved it to the desktop. I believe this package is the same thing as adobe-flashplugin in synaptic). Now, Flash just comes up as a black box in Firefox with no video whatsoever. However, much more interesting is what it does in Epiphany: It plays the video without sound, but saves a file to my temp folder which can be played as a video and which has sound and is better quality that the video online. 
Alright magic computer geeks--any advice? (don't take that the wrong way, I assure you that I am a huge geek as well, just not with computers).
-finley
p.s. Sound works on my computer, just not online. I have checked Alsa as well, and Master and PCM are up all the way.

---

### Post by loren41 on 2010-07-29
Finley, I have the same problem after upgrading from 9.1.  All my sound controls are on high and none are muted.  Latest failure was a tutorial produced using Camtasia and running on Firefox.  Need help!  Videos in Firefox have no sound.

---

### Post by loren41 on 2010-07-30
The libflashsupport download in the Forum fixed my problem.:)

---

### Post by finley on 2010-07-31
I'm sorry, am I missing out on some sort of code? What do you mean the libflashsupport plugin in "the Forum". Exactly where is it?

---

