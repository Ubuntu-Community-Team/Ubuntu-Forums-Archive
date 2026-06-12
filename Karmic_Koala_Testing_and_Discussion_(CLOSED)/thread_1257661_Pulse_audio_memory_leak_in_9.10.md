---
title: "Pulse audio memory leak in 9.10"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Frogling on 2009-09-04
Not sure if this is the place to post.

Pulse audio routinely accumulates over 2GB of memory used over a couple of hours.  I realize that this is an early release of Ubuntu, but this appears to be a fairly major issue.

I have attached the output of lshw.

The output of `pulseaudio --version` is: pulseaudio 0.9.16-test6-3-g57e1

I will be checking back fairly regularly to see if any other info is requested.

Thanks

---

### Post by Yellow Pasque on 2009-09-04
You'll want to report this on Launchpad, where you'll probably be instructed to run  valgrind:  [https://wiki.ubuntu.com/Valgrind](https://wiki.ubuntu.com/Valgrind)

---

### Post by Frogling on 2009-09-04
Thanks.

This is the first major issue I have had with ubuntu that wasn't solvable with google.

---

### Post by |Porsche on 2009-09-04
Wow, please let us know the bug# because if that bug is not fixed before release date I am staying away from 9.10. Pulseaudio is already a headache! I don't want any more.

---

### Post by Frogling on 2009-09-04
Submitted to launch pad.

[https://bugs.launchpad.net/bugs/424655](https://bugs.launchpad.net/bugs/424655)

---

### Post by |Porsche on 2009-09-04
Thanks! Just subscribed to the bug.

---

