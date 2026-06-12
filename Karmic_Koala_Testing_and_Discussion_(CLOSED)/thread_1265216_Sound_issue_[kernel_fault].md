---
title: "Sound issue [kernel fault?]"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pedrogfrancisco on 2009-09-13
I've an issue which is weird:
when I'm NOT playing any sound file, the speakers on my laptop do, on random intervals, that weird noise they usually do when the system boots up [I guess when the kernel audio modules are loaded].

When I'm playing some file, the speakers don't do the sound, or if they do, I don't hear it.


Also, my laptop has a led which is supposed to be red when the audio card is muted and blue when it isn't. On previous Ubuntu versions it'd be blue all the time, now it's also randomly red or blue.

Module: snd_hda_intel

Any ideas on how to further diagnose the problems, logs I might check, that kind of stuff?

I need to find out exactly what the module is doing to trigger these two "random" behaviors before I can fill in a bug report.

---

### Post by MacUntu on 2009-09-13
> From: Daniel Chen <>
To: ubuntu-devel-discuss <ubuntu-devel-discuss@lists.ubuntu.com>,
       Ubuntu Devel <ubuntu-devel@lists.ubuntu.com>
Subject: Recent changes to ALSA for power saving
Date: Tue, 26 May 2009 23:18:17 +0200

Hi all,

Luke and I have just pushed a one-line change to 9.10's
/etc/modprobe.d/alsa-base.conf that enables HDA controllers to power
down their amps after ten idle seconds. This change anticipates the
larger power-savings objectives for 9.10.

We expect there will be regressions in the form of audible pops when
the AMPs power down (and/or up). If you experience this symptom in
9.10, please file a bug using "ubuntu-bug alsa-base". Be sure to
change the summary of the bug afterward to "[9.10 regression] HDA
power_save=10".

Thanks,
Dan

So I'd follow that and report it like described.

Daniel Chen later asked to test a patched kernel which fixed the problem for me but I haven't seen any news since then.

If you temporarily want to fix it, just revert that one-liner in /etc/modprobe.d/alsa-base.conf (IIRC it was the last line you have to uncomment - something with "power_save=10").

---

### Post by pedrogfrancisco on 2009-09-13
[ubuntu-bug isn't working here so won't fill it for now]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/405378") as I assume they require all the info only ubuntu-bug can provide sanely, but THANKS a LOT for the info, will use it as soon as possible :)

---

### Post by pedrogfrancisco on 2009-09-13
Found an unofficial patch for ubuntu-bug, reported the alsa-base bug. [#428788]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/428788")

---

