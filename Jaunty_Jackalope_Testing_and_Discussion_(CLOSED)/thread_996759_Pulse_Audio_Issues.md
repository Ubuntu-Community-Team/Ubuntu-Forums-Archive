---
title: "Pulse Audio Issues"
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-11-29
I noticed this:

Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
Nov 29 22:23:33 PPP pulseaudio[6193]: core-util.c: setpriority(): Permission denied
Nov 29 22:23:33 PPP pulseaudio[6193]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 29 22:23:34 PPP pulseaudio[6210]: pid.c: Daemon already running.

So I added that group to my accountL

Adding user `nullack' to group `pulse-rt' ...
Adding user nullack to group pulse-rt
Done.
nullack@PPP:~$ groups nullack
nullack adm dialout cdrom audio plugdev lpadmin pulse-rt admin sambashare

**Q1: Since I did an upgrade over 8.10, what is the default config from an alpa 1 install?**

I notice Im getting audio skipping on playback of multimedia. If I try to disable pulse audio all together in the sound menu by selecting alsa instead of auto detect or pulse, audio results in the error message :

"Could not get/set settings from/on resource"

**Q2: How do I enable ALSA over pulse?**

Thanks

---

### Post by Bou on 2008-11-29
> **Nullack said:**
> I notice Im getting audio skipping on playback of multimedia

Is that like a flapping sound when you play stuff really loud? Or just nothing sounding at all?

---

### Post by psyke83 on 2008-11-29
> **Nullack said:**
> I noticed this:

Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Nov 29 22:23:33 PPP pulseaudio[6193]: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
Nov 29 22:23:33 PPP pulseaudio[6193]: core-util.c: setpriority(): Permission denied
Nov 29 22:23:33 PPP pulseaudio[6193]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 29 22:23:34 PPP pulseaudio[6210]: pid.c: Daemon already running.

So I added that group to my accountL

Adding user `nullack' to group `pulse-rt' ...
Adding user nullack to group pulse-rt
Done.
nullack@PPP:~$ groups nullack
nullack adm dialout cdrom audio plugdev lpadmin pulse-rt admin sambashare

**Q1: Since I did an upgrade over 8.10, what is the default config from an alpa 1 install?**

I notice Im getting audio skipping on playback of multimedia. If I try to disable pulse audio all together in the sound menu by selecting alsa instead of auto detect or pulse, audio results in the error message :

"Could not get/set settings from/on resource"

**Q2: How do I enable ALSA over pulse?**

Thanks

System/Preferences/Sound will *only* control GStreamer applications (Totem, Rhythmbox, GNOME-blessed apps). All other programs ignore the settings you choose here.

Furthermore: the ALSA libraries have been patched in Intrepid onwards. If a PulseAudio server is detected as running, then ALSA output is transparently mapped to PulseAudio via the PA ALSA plugins. In practice, this means that choosing "ALSA" output in System/Preference/Sound won't make too much of a difference (sound will still get remapped to the PulseAudio server).

This is a UI problem - but it's the fault of the Sound Properties application (which gives the false impression of being a system-wide arbiter of sound settings) as much as PulseAudio.

RE: Skipping, I suggest you read the recent threads on PulseAudio. Many people notice stuttering in PA 0.9.13 (in Luke's Intrepid PPA, Jaunty, Fedora 10...)

To answer Q2, the enable "true" ALSA output, you must kill the pulseaudio server (not recommended). Adding a startup item to the GNOME Session (pkill pulseaudio) is enough, but it's definitely not recommended.

Have you ensured that your PulseAudio configuration is correct? See my [Fixes]("http://ubuntuforums.org/showthread.php?t=789578") thread (just ignore the parts dealing with Hardy/Intrepid). You should also consider troubleshooting sound via the PA utilities rather than ALSA (unless you're sure it's a kernel issue).

---

