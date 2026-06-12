---
title: "How do I fix sound in my PC? Movies won't play (mplayer)"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by Francisco on 2005-04-08
But I can hear the regular sounds at signon, listen to CD's and MP3's.

 I am trying to playback a movie I downloaded from my windows PC but I get /dev/dsp not found error when initializing.

 How can I find out what module is the one being used at system start? Cause that one works.

 This is my lsmod for sound:

francisco@ubuntu:~ $ lsmod | grep snd
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
francisco@ubuntu:~ $
 
 Thanks

---

### Post by Francisco on 2005-04-08
Also, I want to add I can play movies and hear the movie with VLC, but I cannot do that with Mplayer, esound is the one I should use but it is not on the list.

 See for yourself.

---

### Post by c_dog on 2005-04-08
Mplayer doesn't like the esd deamon. For Mplayer to work you need go into the System>Preferences>Sound menu and uncheck the 'Enable sound server startup' box.

---

### Post by Francisco on 2005-04-10
[QUOTE=c_dog]Mplayer doesn't like the esd deamon. For Mplayer to work you need go into the System>Preferences>Sound menu and uncheck the 'Enable sound server startup' box.[/QUOTE]

 Thanks

---

