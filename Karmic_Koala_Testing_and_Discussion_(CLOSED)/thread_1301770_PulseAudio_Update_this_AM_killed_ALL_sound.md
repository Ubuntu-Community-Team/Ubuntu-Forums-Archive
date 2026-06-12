---
title: "PulseAudio Update this AM killed ALL sound"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frogotronic on 2009-10-26
Hello,

  Upgraded from jaunty to karmic last night - everything went well.  This AM when I did an upgrade, the pulseaudio system was updated and I lost sound.

  It appears that now my sound card is not being detected.  See here: 

  [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/461258](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/461258)

Any Advice?

---

### Post by philinux on 2009-10-26
You got a comment on there requesting you run this.

```
apport-collect -p alsa-base 461258
```

---

### Post by kaivalagi on 2009-10-26
I'm in the same boat, sound card has been fine for the last 3 versions of the OS and in 9.10 RC it is no longer detected - I ran "apport-collect -p alsa-base 461258" to post system details...

---

