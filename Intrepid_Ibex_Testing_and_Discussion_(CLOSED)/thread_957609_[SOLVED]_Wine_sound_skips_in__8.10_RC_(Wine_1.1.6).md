---
title: "[SOLVED] Wine sound skips in  8.10 RC (Wine 1.1.6)"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aaronb on 2008-10-24
Hi there people,

When running Steam > Portal in 8.04 the sound is fine, I have just updated to RC and the sound skips in Portal. I have updated to the latest version of wine from the new Intrepid repository of WineHQ but the sound issue still skips.

I' currently using Wine 1.1.6 (I will post comment once 1.1.7 update is available).

Mobo: 965P-DS3
CPU: C2D 4300
RAM: 2GiB of 6400 (800Mhz)

Thanks in advance for any advice.

---

### Post by hikaricore on 2008-10-24
Open up **winecfg** and check to see if you're using ALSA or OSS.

If nothing is checked in the audio tab try checking ALSA.
If one or the other is checked, uncheck it and try the one that isn't.

I've had mixed results from system to system using ALSA and OSS.

Best of luck.

You also may want to try disabling desktop effects to see if this has any effect on the issue after trying out what I suggested.

---

### Post by aaronb on 2008-10-24
Thanks for the reply.

**winecfg**
ALSA = Skipping / intermittent sound.
OSS = No sound.

Desktop effects are disabled.
The glxgears get about 8000 to 9000 fps.

---

### Post by hikaricore on 2008-10-24
Check to see if there are any sound options ingame that you can mess with.

Aside from that I'm sort of low on ideas today.

---

### Post by psyke83 on 2008-10-24
> **aaronb said:**
> Thanks for the reply.

**winecfg**
ALSA = Skipping / intermittent sound.
OSS = No sound.

Desktop effects are disabled.
The glxgears get about 8000 to 9000 fps.

The stable version of WINE doesn't work well with PulseAudio, but the development version (not in our repositories) is much better.

I have three possible suggestions: a) use Intrepid's stable version of WINE with OSS output **and** the PulseAudio OSS wrapper; b) use the latest development version of WINE with ALSA output; or c) use any version of WINE without PulseAudio.

**a) To use the PulseAudio OSS wrapper:**
[LIST=1]
[*]Go to winecfg and select the "OSS" option, and leave the other sound options to their default (IIRC, Full Acceleration, 44100Khz, 16bit, no driver emulation).

[*]Edit your shortcut to Portal (or Steam, if you do not run it directly), and append "padsp" before the wine command.
[/LIST]

**b) To use the latest development release:**
[LIST=1]
[*]Go to [http://www.winehq.org](http://www.winehq.org) and add the repository to your sources list, and allow WINE to upgrade to the latest development release.

[*]Go to winecfg and select the "ALSA" option, and leave the other sound options to their default (IIRC, Full Acceleration, 44100Khz, 16bit, no driver emulation).
[/LIST]

**c) To use WINE without PulseAudio:**
[LIST=1]
[*]Go to winecfg and select the "ALSA" option, and leave the other sound options to their default (IIRC, Full Acceleration, 44100Khz, 16bit, no driver emulation)

[*]Kill PulseAudio *before* launching either Portal, Steam or any WINE application:
[/LIST]
```
$ pkill pulseaudio
```

I recommend you try option B, but to help you decide:
If you don't want to risk using an unstable version of WINE, try A.
If you like PulseAudio and want a properly configured system, try option B.
If you don't care about PulseAudio and you want a quick method to get sound working properly, try option C.

For more information, see Appendix A and B of my [PulseAudio guide]("http://ubuntuforums.org/showthread.php?t=789578") for Hardy. Also see the [Intrepid]("http://ubuntuforums.org/showthread.php?t=866965") guide if you need to configure PulseAudio.

---

### Post by aaronb on 2008-10-24
Nice post, I will try this tomorrow.
(Time to test vs Sleep :))

---

### Post by aaronb on 2008-10-25
Once again, thank you!

A: Does the trick with just very slight skipping.
B: I have always used the winehq version as most games (that I have) work fine.
C: Does the trick as well.

I have gone with choice C and placed an icon on the panel (And once either pulseaudio is binned or applications get updated I will delete the icon).

---

