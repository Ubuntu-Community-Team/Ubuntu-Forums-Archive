---
title: "Installed Rhythmbox 2.98 from ppa, but get 2.96 when I start it"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by Theeboon on 2012-10-17
Apt-cache policy rhythmbox output is:

rhythmbox:
  Installed: 2.98-0.1~webupd8~precise2
  Candidate: 2.98-0.1~webupd8~precise2

But when I start Rhythmbox, it still gives me 2.96.

Could it be that I have two separate installations of this app? I have no idea.

I'm running precise.

---

### Post by stinkeye on 2012-10-17
Try ```
killall rhythmbox
```
then check again.

---

### Post by Theeboon on 2012-10-17
Thanks but I tried restarting the system as well. "killall rhythmbox" gives me "no process found" right now, but 2.96 stubbornly starts when I type "rhythmbox" or start it from dash.

---

