---
title: "Disable pulseaudio without removal"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tonohono on 2009-03-27
Howdy,

How might I go about disabling pulseaudio in Intrepid, so it no longer interferes with ALSA and applications utilizing ALSA?

In Hardy/Intrepid, running **pulseaudio -k** sufficed. However, running such in Jaunty results in the following message:
```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
```

Even after adding myself to the pulse-rt group and running pulseaudio -k without error, it persists to interfere.

So, save removing pulseaudio, which for some unspeakable reason ubuntu-desktop depends upon, how, if at all, can it be entirely disabled?

Alternatively, is it possible to reliably configure pulseaudio to use surround sound? The howto's I've found thusfar have been wholly unhelpful.

Thanks!

---

### Post by zenithdave on 2009-03-27
This a crude way but go to synaptic search for pulse audio then remove the 'Pulseaudio sound server' i have to do it on install and usually upgrades !!!! and i agree i don't know why it is there at all while its this unstable.

eta don't know about surround sound.

---

### Post by danwood76 on 2009-03-27
Pulseaudio is pretty well integrated into the system so removing it is no longer a simple task.

Setting up surround sound is a lot simpler in the next version of pulseaudio, which is available in a PPA.
[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)
This allows you to choose graphically the output profile through pavucontrol.

You could also setup a surround sound device in your /etc/asound.conf and also in your /etc/pulse/default.pa file.
Obviously the second way is a little harder to get right.

---

### Post by markbuntu on 2009-03-27
You need to be a member of
pulse
pulse-rt
pulse-access

Jaunty is a little more difficult since the devs have set autospawn to yes in /etc/pulse/client.conf so you need to set it to no before you can actually kill pulse.

---

### Post by loomsen on 2009-03-28
If none of the above work, you could gzip it in place, won't be removed not started that way...

At least this worked with prior releases for me, try:
```

sudo gzip /usr/bin/pulseaudio

```

But pulse working for me just fine now, user level, software mixing, just everything.

---

### Post by Tonohono on 2009-03-28
> **markbuntu said:**
> You need to be a member of
pulse
pulse-rt
pulse-access

Jaunty is a little more difficult since the devs have set autospawn to yes in /etc/pulse/client.conf so you need to set it to no before you can actually kill pulse.

Thanks! The setting in **/etc/pulse/client.conf** was the key. It would explain why pulseaudio kept returning from the grave after I killed it. Also, it seems I only needed to be a part of the **pulse-rt** and **pulse-access** groups.


For the record, setting **default-sample-channels** in **/etc/pulse/daemon.conf** to reflect my speaker configuration provided surround sound, but there was a perceptible delay in audio start/stopping... reminiscent of ALSA's early days. Pulseaudio still isn't perfect, but at least it seems to be getting *better*.

---

