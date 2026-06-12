---
title: "Karmic Sound Gone"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tripinva on 2009-06-04
Hello all:

I'm running Karmic Kubuntu with some of the latest updates.  (I downgraded X Synaptics and Intel when my video and touchpad broke, and there are a few others that don't want to install cleanly at the moment.)  I do not have Pulse Audio installed.

I restarted my system after about three weeks of updates, and when it came back up, my speakers were emitting a scratching sound.  Upon logging in, kmix immediately crashed and crashes any time I try to load it.  KDE notifies me that ALC268 isn't working, but any attempts to modprobe snd-hda-intel, while appearing to succeed, don't actually change anything so far as I can tell.  I've tried it with several different models.

I tried booting an old kernel that was known working, but that didn't fix it.  The problem likely lies elsewhere, though I don't know where.

Any ideas?  I'm not sure which files to attach...

- Trip

---

### Post by Zorael on 2009-06-05
Could you try this in a recovery session? Or just generally outside of X.
```
$ speaker-test -twav -c2
```

If it persists even when going back to an older kernel, then you have to have some model options specified someplace that you didn't have earlier (as you said you've tried it with different models).

Else, hardware failure? Does it work in a live cD/usb environment of Jaunty?

---

### Post by tripinva on 2009-06-05
> **Zorael said:**
> Could you try this in a recovery session? Or just generally outside of X.
```
$ speaker-test -twav -c2
```

I used Ctrl+Alt+F1 (if that helps) and it spit a ton of errors at me from different files.  I would have caught the output and attached a log but I couldn't Ctrl+C out of it to do it.  I had to reboot the system, unless there's a better way to escape it I am not aware of.

> If it persists even when going back to an older kernel, then you have to have some model options specified someplace that you didn't have earlier (as you said you've tried it with different models).

I have the whole model line removed at the moment, which is how it had been working in the first place.  I didn't add it until my sound failed.

> Else, hardware failure? Does it work in a live cD/usb environment of Jaunty?

Works in XP, just tested it.

I'd be more patient if the scratching wasn't loud enough to be distracting.  I have another computer on which I'm listening to music; I can live without sound for a short time until something's fixed.  I just can't stand the scratching.

- Trip

---

### Post by yelo3 on 2009-06-05
Try to execute 
killall pulseaudio
then pulseaudio automatically respawns and it's fixed (for me).

---

### Post by davideotape on 2009-06-05
> **yelo3 said:**
> Try to execute 
killall pulseaudio
then pulseaudio automatically respawns and it's fixed (for me).

Thanks for that, fixed mine fine. My audio is being a bit hit and miss sometimes, and is not consistent. Hopefully it'll stabilize soon though :D

---

### Post by yelo3 on 2009-06-05
I don't know the exact cause, but these steps will sometimes trigger my problem:
- hit mute
- wait some minutes
- open the audio player and start playing
- unmute

then killall pulseaudio to fix.
This might be caused by the introduction of power management in the audio kernel module

---

### Post by davideotape on 2009-06-05
> **yelo3 said:**
> I don't know the exact cause, but these steps will sometimes trigger my problem:
- hit mute
- wait some minutes
- open the audio player and start playing
- unmute

then killall pulseaudio to fix.
This might be caused by the introduction of power management in the audio kernel module

I think that having mute on when you shutdown, and hence having mute on at your next boot causes this problem. Time to file a bug?

---

### Post by yelo3 on 2009-06-05
Yes you might right about the shutdown! This always triggers the problem for me!
But it is also triggered in other cases in my laptop (related to muting I think).

File a bug to pulseaudio and past the link! Thanks

---

### Post by davideotape on 2009-06-05
EDIT: Above bugreport is incorrect. Hadn't read all the fine detail before posting.

EDIT: Deleted incorrect bug report. Here is the new one: [https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/384015](https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/384015)

---

### Post by tripinva on 2009-06-05
As I stated in the second sentence of my post, I do not have Pulse Audio installed.

- Trip

---

### Post by tripinva on 2009-06-05
On a whim, I tried to sudo rmmod snd-hda-intel.  It worked, and killed the static sound (finally).  

Normally, it refuses to rmmod it, claiming it's busy.  I usually can't even force it to rmmod.  I don't know what's wrong, but something is.

- Trip

---

### Post by davideotape on 2009-06-06
> **tripinva said:**
> As I stated in the second sentence of my post, I do not have Pulse Audio installed.

- Trip

Maybe installing it will fix the problem? Just a thought...

---

### Post by Zorael on 2009-06-06
> **davideotape said:**
> Maybe installing it will fix the problem? Just a thought...
Um, this seems to be a problem with the alsa module itself, and if installing PulseAudio to act as a sound server working on-top of [the sound module] would make any difference, I'd be very surprised.

---

### Post by tripinva on 2009-06-06
> **davideotape said:**
> Maybe installing it will fix the problem? Just a thought...

As Zorael said, this is screaming driver problem at me.

I refuse to install Pulse.  It doesn't play nice with KDE and caused me nothing but problems until I finally got rid of it.  I've immediately removed it from any system I've installed since then.  I've never seen PulseAudio work properly anywhere I've used it.

- Trip

---

### Post by davideotape on 2009-06-06
Here's a report I've found that might be relevant: [https://bugs.edge.launchpad.net/ubuntu/+bug/383936](https://bugs.edge.launchpad.net/ubuntu/+bug/383936)

---

### Post by tripinva on 2009-06-06
> **davideotape said:**
> Here's a report I've found that might be relevant: [https://bugs.edge.launchpad.net/ubuntu/+bug/383936](https://bugs.edge.launchpad.net/ubuntu/+bug/383936)

Thanks.  I tried adding myself to the audio group, but no success.  Still crashes kmix and still just getting a scratching sound.

I'll be filing a bug report later in the afternoon, I suppose.

- Trip

---

