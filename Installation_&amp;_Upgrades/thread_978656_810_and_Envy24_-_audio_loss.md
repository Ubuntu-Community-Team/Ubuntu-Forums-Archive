---
title: "8:10 and Envy24 - audio loss"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by its_jon on 2008-11-11
Hello friends.

I upgraded to 8:10 online .... everything appears to be working as before except my sound.

My first ever up and running Linux was 8.04.... and I had to download the Envy24 sound stuff in synaptic to get sound.
Sound was AWESOME through my teretec card....

Lost sound with 8:10 upgrade though..... I get the little drum sound on boot at the password screen... then nothing.

I seem to have checked and unchecked everything I can find to do with the Envy24 sound driver UI and also the Ubuntu system/pref/sound options..

Help :)

and Thanks

John
Scotland

---

### Post by its_jon on 2008-11-12
help thanks :)

---

### Post by its_jon on 2008-11-13
If someone could point me towards a thread of relevance that would be great 

thanks

---

### Post by its_jon on 2008-11-15
help :-|

---

### Post by its_jon on 2008-11-15
I read somewhere to type alsamixer into a terminal....

I did....

I got this

&#9474; Card: PulseAudio                                                            
&#9474; Chip: PulseAudio                                                          
&#9474; View: [Playback] Capture  All                                               
&#9474; Item: Master [Off]    


any ideas ?

---

### Post by warbread on 2008-11-15
I just fixed this problem myself.  I have a Delta 1010 and as soon as I went to 8.10, sound became an issue.  It seems that getting rid of Pulseaudio fixes the problem.  I don't know if PA is the problem per-se, but it's yet another reason I hate the shiny new audio server that has been a thorn in my side since it was forced on Ubuntu users.

[Here's the instructions that I followed]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/").  Don't forget to thank the blog poster for their trouble!!

---

### Post by its_jon on 2008-11-18
Thanks for the link.....

followed instructions....

and it simply started to work again :) !!

super !....

If only I actually knew what I did I would feel better about myself......


for now though Im just happy its working... whats pulse anyway ?

---

### Post by warbread on 2008-11-18
> **PulseAudio** (formerly **PolypAudio**) is a [cross-platform]("http://en.wikipedia.org/wiki/Cross-platform"), networked [sound server]("http://en.wikipedia.org/wiki/Sound_server") project. It is intended to be an improved drop-in replacement for the [Enlightened Sound Daemon]("http://en.wikipedia.org/wiki/Enlightened_Sound_Daemon") (ESD).

[From Wikipedia]("http://en.wikipedia.org/wiki/Pulseaudio")

It's not a bad idea, per-se, but I've been fighting with it on my Linux DAW since it became the default sound server in Ubuntu.

---

