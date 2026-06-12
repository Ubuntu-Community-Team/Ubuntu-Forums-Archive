---
title: "warning: suspend fails and borks pulseaudio pacmd"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nanog on 2010-01-15
suspend fails and causes pulseaudio pacmd process to run at 100%.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/507941](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/507941)

```
killall pulseaudio
``` seems to fix the problem.

---

