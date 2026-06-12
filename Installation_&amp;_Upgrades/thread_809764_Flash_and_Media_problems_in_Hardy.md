---
title: "Flash and Media problems in Hardy"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by DAE_JA_VOO on 2008-05-27
Since moving to Hardy a few weeks ago, i've been having serious issues. This is a fresh install.

Once the machine has started, if i open a video file or an MP3, they work perfectly, but if i open my browser and go to a site like youtube, the videos don't work.

If i then restart, and open a youtube video FIRST, it works, but them my media doesn't.

What the hell is going on?

---

### Post by CameO73 on 2008-05-27
That's a problem caused by PulseAudio (the new sound system in Hardy) and Flash. Flash will take complete control of all audio and won't share with any other audio source (or, if any program has control, it just won't play videos).

There are various bug reports on this (most noticably [this one](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)), but the problem lies with the (closed source) Flash plugin. So were just waiting for Adobe to fix this.

The normal way to solve this problem would be to use the **libflashsupport** package in Synaptic. This will fix the sound issues, but will crash Firefox a lot more. The best solution at the moment (at least until Flash 10 comes out), is [explained here](http://ubuntuforums.org/showthread.php?p=4928900). 

By the way, I've been playing a lot with this issue lately and found that the most stable combination is Firefox 3 RC1 and Flash 10 beta. This means that eventually this problem will be solved (when Firefox 3 final and Flash 10 are released).

---

### Post by DAE_JA_VOO on 2008-05-27
Thanks for the reply.

Okay well i've just done that fix and it didn't help, at all.

---

### Post by markbuntu on 2008-05-27
I can confirm some of that. Firefox 3 rc 1 fixes those problems so just hang on a little until it is available as an update. I have not tried the Flash 10 beta so I can't say if that necessarily fixes your problem.

You might try getting the pulseaudio and xmms ALSA wrappers which makes all pulseaudio and xmms audio go through ALSA. Search alsa in synaptic and you will find them. Then make sure you have alsa selected for everything instead of automatic in System/Preferences/Sound. 

If you have more than one sound card you can also find the little tiny package that lets you choose your default alsa sound card. It will reside in System/Preferences It can reduce confusion when deciding which driver to use in Sound, just choose ALSA.

I did all that and it works for me. I can have rythmbox streaming internet radio and if I watch a video in firefox I get both in my speakers. One small thing, if I am watching a video on like youtube and start rythmbox,flash shuts it out but after the video is over I can start rythmbox up again and it works fine.

---

