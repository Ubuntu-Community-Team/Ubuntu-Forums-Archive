---
title: "Sound problem: too much bass"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-03-20
I usually don't play music on my testing machines, so I didn't notice that my audio output is broken: too much bass (like my speakers are used as subwoofers). It does not sound overdriven like when you raise the volume too high, just the bass level is abnormal high.

First thing I do in such situations: create a test user. Test user's output is normal, so it's user dependent. I remembered installing psyke83's PA equalizer some time ago - purged it, no effect. I also removed everything PA-related in my home dir, no effect.

Any ideas?

---

### Post by MacUntu on 2010-03-20
Oh, great. This actually was just a problem with Banshee.

Removing
```
~/.config/banshee-1/equalizers.json
~/.config/banshee-1/equalizers.xml
```
fixed it (equalizer was set to neutral within banshee).

:)

---

### Post by derekeverett on 2010-03-20
I didn't know there was a such thing as too much bass ?!
;)

---

### Post by MacUntu on 2010-03-20
Depends only on the speakers. :D

---

