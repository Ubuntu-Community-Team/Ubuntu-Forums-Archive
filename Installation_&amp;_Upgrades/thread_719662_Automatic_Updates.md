---
title: "Automatic Updates"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by ShinHadoken on 2008-03-09
How do I automatically update *everything *on my system? Can I do it through Synaptic or do I need to write a script?

---

### Post by taurus on 2008-03-09
You can always run these from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by vishzilla on 2008-03-09
Ubuntu has an Update manager which will intimate whether your system needs updates. You need to check if you have enabled Ubuntu updates (gutsy-security and gutsy-updates) at System->Admin->Software Sources->Updates

---

### Post by ShinHadoken on 2008-03-11
bump (thanks guys) I know that you can run those commands from the terminal, I just want to know how to do this automatically. Can I put those commands in a script? Or can I use Synaptic to automatically update everything?

---

### Post by vikrant82 on 2008-03-11
I use cron to get automatic update notifications. Go [here.]("http://kakku.wordpress.com/2008/03/11/cron-and-crontab-the-easy-and-useful-scheduler/")

---

