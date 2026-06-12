---
title: "No sound, pulseaudio uses up to 65% CPU"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2009-09-09
Hello all,
With the release of alpha5 sound stopped working for me.
Pulseaudio is using up to 65% and is seriously slowing down the system.
I reported this bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/425918](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/425918), so far no comments.
Does anyone have an idea how to solve this?
Thanks in advance! :P

---

### Post by mfox on 2009-09-09
See [this]("http://ubuntuforums.org/showthread.php?t=1168194") thread.  In a nutshell, removing pulseaudio solved sound problems for several of us in Karmic.

---

### Post by rubenverweij on 2009-09-12
Thanks for your reply mfox.
I purged pulseaudio, with the new update it got itself installed again and everything works flawlessly now! :popcorn:

---

### Post by plun on 2009-09-12
A pkill solved it for me and after that using [pavucontrol]("http://packages.ubuntu.com/karmic/pavucontrol") for unmute and adjusting volume
```

pkill pulseaudio; sleep 2; pulseaudio -vv
```

Gnome volume control seems to be broken.....

---

