---
title: "Kubuntu Intrepid: mixing KDE and flash sound apps?"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LadFromWales85 on 2008-09-30
Having recently upgraded to Intrepid, things haven't been too bad, few niggles here and there, but this one issue is just proving to be a nightmare!

I have no problems running multiple different KDE applications with sound, Kopete, Kaffeine, Amarok can all make sound at the same time with no issue.
Throw Flash into the mix and it cannot make sound.
Gstreamer apps appear to be able to produce sound fine.

If I close the KDE apps playing sound, after a short while, Flash can make sound, but starting Amarok or Kaffeine will show Xine error initialising sound card.

Running Firefox from a console, I can see that it is showing errors relating to ALSA and Pulse when Flash attempts to output sound

```
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default

```

I had a look at the distilled Pulse thread, but it shows that it is only for Ubuntu rather than Kubuntu.  I have Gnome installed, but I use KDE.

Is there a fix for this issue at the moment?  I've not looked at launchpad yet, just trying here first!

Thanks for any advice. :KS

---

### Post by TWO on 2008-10-14
> **LadFromWales85 said:**
> Having recently upgraded to Intrepid, things haven't been too bad, few niggles here and there, but this one issue is just proving to be a nightmare!

I have no problems running multiple different KDE applications with sound, Kopete, Kaffeine, Amarok can all make sound at the same time with no issue.
Throw Flash into the mix and it cannot make sound.
Gstreamer apps appear to be able to produce sound fine.

If I close the KDE apps playing sound, after a short while, Flash can make sound, but starting Amarok or Kaffeine will show Xine error initialising sound card.

Running Firefox from a console, I can see that it is showing errors relating to ALSA and Pulse when Flash attempts to output sound

```
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default

```

I had a look at the distilled Pulse thread, but it shows that it is only for Ubuntu rather than Kubuntu.  I have Gnome installed, but I use KDE.

Is there a fix for this issue at the moment?  I've not looked at launchpad yet, just trying here first!

Thanks for any advice. :KS

Hello

I'm using Kubuntu Intrepid Ibex Beta 1 with KDE 4.1.2. 

Anyway, I'm neither getting any sound from flash videos nor any output from the Konsole whilst I run Firefox through it.

Sound is working in Amarok, but system sounds and flash aren't working at the moment.

Did you manage to find a fix yet?

TWO

---

### Post by LadFromWales85 on 2008-10-14
Seems to have fixed itself!
All I've done is deleted my .asound from profile and the asound.rc from /etc

I can run Amarok or Kaffeine and play Flash in browser at the same time.  To be honest I've spent very little time at my pc the last few days, and have only been updating when it'd result in clean updates without held packages, so I'm not sure what packages have updated which have sorted the problem for me.

I'd love to know what fixed it so I'll know for next time!

---

### Post by TWO on 2008-10-14
> **LadFromWales85 said:**
> Seems to have fixed itself!
All I've done is deleted my .asound from profile and the asound.rc from /etc

I can run Amarok or Kaffeine and play Flash in browser at the same time.  To be honest I've spent very little time at my pc the last few days, and have only been updating when it'd result in clean updates without held packages, so I'm not sure what packages have updated which have sorted the problem for me.

I'd love to know what fixed it so I'll know for next time!

That's good to hear. Wish I was able to try and solve mine but my Intrepid Beta has decided not to allow me to get to the login in screen no matter what I do so I am faced with reinstalling it yet again! 'tis tough work, development versions!

---

### Post by xerosis on 2008-10-15
See I have the same problem but I have neither I have no asound conf files in home or /etc, I'm kde-only, any ideas?

---

### Post by dabl on 2008-10-15
> **xerosis said:**
> 

 I have no asound conf files in home 

That is the "hidden" file .asound.

With Dolphin or Nautilus or whatever file browser you are using, choose "View > Show Hidden Files" to see the files that begin with a period in your home folder.  :)

---

