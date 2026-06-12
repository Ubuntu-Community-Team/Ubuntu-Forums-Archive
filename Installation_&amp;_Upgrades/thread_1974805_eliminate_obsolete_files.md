---
title: "eliminate obsolete files?"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by telegiovi on 2012-05-06
When I was upgrading to ubuntu 12.04, a window asked me if I wanted to cancel 104 obsolete files. I had no time and did not cancel the files. Can I do it now? The new ubuntu is already running. How could I do?
Thanx

---

### Post by Paddy Landau on 2012-05-07
You probably don't have a problem unless you have very old hardware with a tiny hard disk.

However, you can open a terminal and enter the following two commands to clear out old installation files and redundant installed applications:
```
sudo apt-get autoremove
sudo apt-get clean
```

---

### Post by telegiovi on 2012-05-08
Thanks

---

### Post by Paddy Landau on 2012-05-08
If this has resolved your question, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

