---
title: "Skype Speaker Buzzing"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by Cu Rua on 2014-05-17
Using Ubuntu 14.04, if I send a chat message in Skype, the speakers start making a monotone buzzing whine that's very loud. Muting turns the sound off. How do I fix this issue?

---

### Post by sonny6 on 2014-05-28
I have the same annoying problem. Anyone know how to fix this?

---

### Post by MirkoCe on 2014-05-29
Have you tried launching skype with

```
env PULSE_LATENCY_MSEC=30 skype
```

If it works fine you can edit the launcher to always start skype like that

---

