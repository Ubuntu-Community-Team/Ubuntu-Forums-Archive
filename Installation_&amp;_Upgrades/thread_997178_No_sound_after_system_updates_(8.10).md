---
title: "No sound after system updates (8.10)"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by fili on 2008-11-29
After a recent system update (which included a new kernel) I can't seem to get any sound out of my speakers.
I've never had any problem with this before, and this box has been running Ubuntu since version 6.

> 
**$ uname -r**
2.6.27-7-generic

**$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**$ lspci**
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

I've tried everything relevant in [this post]("http://ubuntuforums.org/showthread.php?t=205449") and also tried other obvious stuff like connecting alternate speakers and checking the levels in alsamixer.
Alas, all to no avail.

It would probably be fixed by reinstalling 8.10, but I'm not very keen to do that just yet. Does anyone have any suggestions to resolve this issue?

Thanks in advance.
Fili

---

### Post by fili on 2008-11-29
I just followed this [PulseAudio troubleshoot guide]("http://ubuntuforums.org/showthread.php?t=789578") without any luck.

In 'Appendix A' I ended up with option C

> C. The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.


My PCM/Master volumes are not muted.
Since it happened after a kernel update, I'm betting on the ALSA kernel-module being the cause.
How can I reinstall/rebuild this module?

---

### Post by ravalox on 2008-11-29
I am having this exact problem, I removed pulseaudio with still no luck.  Short of installing Fedora 10 I am out of ideas.

---

### Post by fili on 2008-12-01
*bump*

---

### Post by Clive32 on 2008-12-01
I thought i was the only one with this problem.
I have tried what i know, but no luck at all.

---

