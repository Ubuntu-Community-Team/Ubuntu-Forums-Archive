---
title: "Pulse Audio Memory Leak"
date: 2010-01-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vgrisham on 2010-01-11
I am curious if the evil UDEV/Pulse Audio memory Leak [bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655") is showing up in Lucid? It has made Karmic a no go on my System 76 Pangolin.

---

### Post by RAOF on 2010-01-11
From the bug report it looks like the answer is “no, it hasn't been (deliberately) fixed”.  Try a LiveCD though; maybe it's been fixed by accident.

---

### Post by jdayrutherord on 2010-01-16
Yes, it is still there in the next release. I tried it on my
system76 daru laptop, and initially I thought it might have been fixed but
it showed up. Its also in Fedora 12, which I am running now. It has the
same issue, but seems to be a little lighter on the cpu than 9.10 was, though I never really tried to document that. (and the Admin, services module is still there).

I didn't see this on 32-bit amd, nvidia desktop that I setup. I am not sure if its a 64bit issue or the Intel sound chips, I suspect the Intel.

---

### Post by jdayrutherord on 2010-01-16
Yes, it is still there in the next release. I tried it on my
system76 daru laptop, and initially I thought it might have been fixed but
it showed up. Its also in Fedora 12, which I am running now. It has the
same issue, but seems to be a little lighter on the cpu than 9.10 was, though I never really tried to document that. (and the Admin, services module is still there).

I didn't see this on 32-bit amd, nvidia desktop that I setup. I am not sure if its a 64bit issue or the Intel sound chips, I suspect the Intel.

---

### Post by vgrisham on 2010-01-17
Ding dong the witch is gone! Leak fixed! Woo hoo, I'm on Karmic. Finally! I got impatient with my media center and installed Windows 7 though. Gulp.

Edit: To get the fix, you'll need to turn on Karmic Proposed on the Update tab under Software Sources in Synaptic.

---

### Post by Naegling23 on 2010-01-26
so the memory leak is fixed in karmic?  What files exactly do I need when I enable the proposed updates?  I'd prefer to update only the necessary files, then turn proposed off to keep from causing any additional problems.

---

### Post by vgrisham on 2010-01-26
According to the [bug report]("https://bugs.launchpad.net/ubuntu/karmic/+source/pulseaudio/+bug/424655/+editstatus"), the file to update is module-udev-detect. I've left my Proposed repository open since the fix was released, and have had no problems (but then, it would be difficult imho for Karmic to get *more* buggy).

---

### Post by dino99 on 2010-01-27
for a few days i've had troubles with sound, wine and memory crash. at first glance it was a problem with alsa/pulse, so i purged and reinstall several times without success.
In synaptic, i've found a prog named "bleachbit" to clean your system. And it does very well (take care because it's so powerfull).

Then, all the troubles are gone.

note: bleachbit used as admin (system tools menu)

---

