---
title: "Bug #273693 &quot;biarch alsa-lib path problem with Skype&quot;"
date: 2008-12-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Richard on 2008-12-21
This bug "biarch alsa-lib path problem with Skype" [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693)
seems reappear with Alsa new version.
I got the same error with native 32 bits OpenGL Games on Jaunty amd64 :
> ALSA lib ../../src/conf.c:2700: (snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2196: (snd_pcm_open_noupdate) Unknown PCM default.

Someone else with this error ?

---

### Post by alexv75 on 2008-12-21
Yeah :( . I just posted about it in launchpad:

+1 - same problem, Doom 3, ETQW, Quake 4 and Skype do not have sound, Prey however works somehow... I'm using 64Bit Jaunty.

Doom and the others:

------ Alsa Sound Initialization -----
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: No such file or directory
dlclose
--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------

Prey:

------ SDL Sound Initialization ------
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default
SDL is using audio backend 'esd'.
allocated a mix buffer of 32768 bytes
SDL_AudioSpec: 44100 freq, S16LSB, 2 channels, 512 samples.
Opening audio device...
Audio device is ready.
--------------------------------------

I seriously hope a fix gets out soon, i need my games :D (none of the previous workarounds works).

---

### Post by Richard on 2008-12-28
There is a workaround taken from comment 5 [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/5](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/5) to disable use of PulseAudio.

---

### Post by alexv75 on 2008-12-28
OMG, thank you so much for the link.. I've read all the posts there, but somehow missed this one. Now everything works, but there is some strange clicking noise every now and then... Meh, i can live with it until a permanent solution is found for the pulseaudio saga.

---

### Post by Pagnol on 2009-01-01
Hello,

I face the same problem. But since I cannot start the GUI, I cannot disable the use of Pulse Audio. Could someone kindly pass me a configuration file of Skype which deactivates the use of Pulse Audio right from the start? Maybe this idea isn't useful at all.

---

