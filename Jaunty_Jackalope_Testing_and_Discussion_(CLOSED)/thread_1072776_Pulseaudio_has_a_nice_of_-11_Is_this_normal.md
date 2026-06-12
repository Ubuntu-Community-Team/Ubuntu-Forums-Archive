---
title: "Pulseaudio has a nice of -11 Is this normal?"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-02-17
Pulseaudio is giving me problems by hanging the system quite often and all I can do is wait for it to stop doing whatever it's doing, which takes about 10-15 secs.
Cheers, Mike

---

### Post by OliW on 2009-02-17
Odd. Mine is 0 but is very stuttery. I just tried renicing it to -11 but that didn't help me.

Try changing yours to something "nicer":

```
sudo renice -1 -p <its PID>
```

---

