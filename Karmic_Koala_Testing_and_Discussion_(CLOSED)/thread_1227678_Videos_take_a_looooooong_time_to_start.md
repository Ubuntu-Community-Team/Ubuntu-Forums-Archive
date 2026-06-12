---
title: "Videos take a looooooong time to start"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-07-30
Hi,

Since I started using Karmic, I've been noticing that launching videos takes a long long time, during which totem even becomes unresponsive.

I'd like to know if this happens to you too, thanks guys.

---

### Post by psyke83 on 2009-07-30
> **Bou said:**
> Hi,

Since I started using Karmic, I've been noticing that launching videos takes a long long time, during which totem even becomes unresponsive.

I'd like to know if this happens to you too, thanks guys.

See: [http://ubuntuforums.org/showthread.php?p=7606764](http://ubuntuforums.org/showthread.php?p=7606764)

---

### Post by Bou on 2009-07-31
Are they related for sure? The other thread doesn't say anything about totem, it's about nautilus (although video files seem to cause both problems).

How do you guys cope with this? Is there a known workaround?

---

### Post by psyke83 on 2009-07-31
> **Bou said:**
> Are they related for sure? The other thread doesn't say anything about totem, it's about nautilus (although video files seem to cause both problems).

How do you guys cope with this? Is there a known workaround?

Definitely. The problem is triggered when opening large video content that is thumbnailed (totem and vlc are both affected, for example).

The workaround is to disable video thumbnailing in nautilus - it's all in the bug report.

---

### Post by Bou on 2009-07-31
Wow, I didn't think disabling an option in nautilus would help totem's performance! I thought that was only to help with the nautilus problem, thanks psyke.

---

### Post by meborc on 2009-07-31
> **Bou said:**
> Wow, I didn't think disabling an option in nautilus would help totem's performance! I thought that was only to help with the nautilus problem, thanks psyke.

well, the problem was never in totem... the problem was that the thumbnail kept indexing/using the video, using all the resources, leaving totem pending and waiting until nautilus has finished

or that is what i imagine happened

---

