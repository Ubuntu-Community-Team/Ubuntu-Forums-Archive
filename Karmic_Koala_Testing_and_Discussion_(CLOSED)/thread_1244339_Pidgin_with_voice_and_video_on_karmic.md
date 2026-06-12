---
title: "Pidgin with voice and video on karmic"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fireman biff on 2009-08-19
I'm trying to build Pidgin 2.6.1 but when I run the configure script it the output near the end include this line:
```
Build with voice and video.... : no
```

I have already installed libgstfarsight0.10-dev, libgstreamer0.10-dev libnice-dev - does anybody know what other libraries need to be install to use voice and video?

---

### Post by fireman biff on 2009-08-19
Nevermind, I figured it out. I needed libgstreamer-plugins-base0.10-dev

---

### Post by riazrahaman on 2009-08-20
Is voice and video working on 2.6.1?

---

### Post by udit1233 on 2009-08-20
hey......is voice and video working in pidgin??????????

---

### Post by fireman biff on 2009-08-20
> **riazrahaman said:**
> Is voice and video working on 2.6.1?

After I got all the dependencies sorted out, it said it installed properly with voice and video support. But when I tried to run pidgin it complained that it couldn't find libpurple so it wouldn't start and I gave up and reinstalled from the repository.

I might try again sometime, or just wait for the repository to update.

---

### Post by eldragon on 2009-08-20
it works... but it doesnt.

vocie worked ok but it was feeding the mic with what came out of the speakers and this made the conversation quite annoying. (same setup, with skype does not have this problem)

trying to do a video conference nuked pidgin here. :(

---

