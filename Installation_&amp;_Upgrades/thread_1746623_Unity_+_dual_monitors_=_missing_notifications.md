---
title: "Unity + dual monitors = missing notifications?"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jay-dubb on 2011-05-02
Hey everyone, I recently did a fresh install of Ubuntu 11.04 on my desktop, and I've recently noticed that the notification bubbles always pop up on my secondary monitor instead of my primary. However, if I log in using Ubuntu Classic (Gnome 2.x), the notifications show up on the correct monitor.

So is this happening to anyone else? My comp. uses an integrated nvidia 9100 chipset and I'm using their propriety driver - can anyone w/ an AMD chipset confirm if it's working for them or not?

---

### Post by Blasphemist on 2011-05-02
What you describe is where mine show but that is fine for me as that is what I'm actually working on most often. I have an Intel gpu.

---

### Post by blueeyesmike on 2011-05-04
Same here dual monitors with an nvidia 9600gt. Anyone know of a way to change this back? I rarely focus on my second monitor and miss notifications now.

---

### Post by comminus on 2011-05-04
You can set a gconf key for notify-osd to make the notifications follow focus. This means that if an application in monitor 1 has focus, the notification will appear in monitor 1.

run the following in a terminal:
```
gconftool-2 -s -t string /apps/notify-osd/multihead_mode focus-follow
```

then press alt+f2 and restart Unity with the following command:
```
unity --replace
```

it may not be required to restart Unity, however these are the steps I've taken to make this work.

---

### Post by lilacsunbird on 2013-01-03
> **comminus said:**
> You can set a gconf key for notify-osd to make the notifications follow focus. This means that if an application in monitor 1 has focus, the notification will appear in monitor 1.

run the following in a terminal:
```
gconftool-2 -s -t string /apps/notify-osd/multihead_mode focus-follow
```

then press alt+f2 and restart Unity with the following command:
```
unity --replace
```

it may not be required to restart Unity, however these are the steps I've taken to make this work.

This trick does not work in 12.10

---

### Post by overdrank on 2013-01-03
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

