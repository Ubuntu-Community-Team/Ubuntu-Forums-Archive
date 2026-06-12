---
title: "Partiotioner not showing in Xubuntu"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by tresoldi on 2006-07-13
I had some problems installing Xubuntu 6.06, and the solution came in a very unexpected way. The installation program worked perfectly until the time the partitioner should be shown: no matter how much I waited (three hours at most), the embedded partitioner (I guess it is GParted) never actually showed up -- my guess was that it was not even being loaded.

By coincidence, I found out that the partitioner did show up when some other program was running (at first I was running only the installer). I tried Firefox and Gaim: both made the installer work, which makes me think it is related to GTK+.

In short, hoping that it might be useful for others, if you are installing (X)Ubuntu 6.06 and think that the embedded partitioner is too slow or that it won't show up, try opening a GTK+ program (preferably Firefox) before launching it. It worked for me, or it was a strange coincidence.

Tiago Tresoldi

---

