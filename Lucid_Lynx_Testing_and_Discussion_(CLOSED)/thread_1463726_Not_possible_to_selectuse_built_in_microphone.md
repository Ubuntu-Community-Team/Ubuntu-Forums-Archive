---
title: "Not possible to select/use built in microphone"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fab.head on 2010-04-27
Hi there,

I have just installed LL RC and it seems that it is not possible to choose between the built in microphone and an external mic (HP laptop, model DV9850EL).

Only the external microphone is enabled by defaul.
If I open **System > Preferences > Sound > Input** there is no selection box for internal and external mic.

The selection was possible (and working fine) under Karmic, but now I cannot choose the input source at all.

```
lspci | grep Audio
``` 

The above code gives me the following:

> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Is there any setting which can help bringing my built in mic back to life?

Or could this be a bug in pulseaudio/alsa?

---

### Post by dino99 on 2010-04-27
install gnome-alsamixer

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by fab.head on 2010-04-27
> **dino99 said:**
> install gnome-alsamixer

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I've tried gnome-alsamixer already, but unfortunately it didn't help.. :(

---

### Post by fab.head on 2010-04-27
After some research, I've found out that in Ubuntu 10.04 there is no possibility to manually select either the internal or the external mic but autoswitching is done based on jack presence (i.e. when an external mic jack is plugged in, the internal microphone is muted and only the external one works; and when no external mic is plugged in, the internal microphone should work).

Anyway, in my case an external microphone connected to the 1/8" jack input works but when I disconnect it, the internal mic doesn't work at all.

---

### Post by ariismail on 2010-04-27
I also have the same problem with my Samsung X360. But in my case, I want to use the external microphone. By default, both microphones are working and I hear noise which is recorded by the built-in microphone. The same command gives 

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

in my Ubuntu 9.10.

I installed Audacity and tried "pulse", "default" or "HDA Intel" separately with all combinations I did with alsamixer. When I enable the capture device in alsamixer (equivalently gnome-alsamixer or kmix) I get both of the microphones working. When I disable it, both microphones are silent. In Gnome's sound panel, there is no option to separate the input devices. I've read the posts in this forum to disable the built-in microphone but when I disable it, both microphones are off.

By the way, I also installed JACK control but as far as I see, it is irrelevant. 

I look forward to use Ubuntu to prepare some podcasts (without noise or post-processing to remove noise with a software). If you have experienced the same problem and have a solution, I would appreciate your help.

Best,
&#304;smail

---

### Post by fab.head on 2010-04-29
I've just filed a bug report here: 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/571294]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/571294")

---

