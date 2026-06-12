---
title: "updates will not complete"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by destratton on 2011-08-24
I have been having this problem for quite awhile. I can download a little better than half of the updates at which point I get the error that update failed. It tries to tell me I am not connected to the internet, which I am. What do I need to do here? Thanks. David

---

### Post by wojox on 2011-08-24
Run this in the terminal and post back the response in code tags:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by Ginzell on 2011-08-24
I'm curious about this too. I had it happen when I was going through the update manager and it kept just closing and not letting me install anything, so I went in through Synaptic and installed what I could, it asked did I want to skip the "problem" I said yes.  Then I went back into update manager (where there was only a few that hadn't installed) and installed what was left, one by one, and for some reason, it worked.  I don't know what it was.

---

