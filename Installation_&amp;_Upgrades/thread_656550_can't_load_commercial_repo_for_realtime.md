---
title: "can't load commercial repo for realtime"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2008-01-02
I tried

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

But I was told it's obsolete.

Is there a better way? I'm trying to get at Realtime 10. Tried all the ways suggested in the forum but it seems that accessing the commercial repo is the key.

---

### Post by oldos2er on 2008-01-02
Do you mean Realplayer? You don't really need a repo. Download it here: [http://www.real.com/linux/](http://www.real.com/linux/)

---

### Post by zvacet on 2008-01-02
Replace that line with **deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner**

---

### Post by arnicainthemembrane on 2008-01-02
gotcha. Still no realplayer tho'. How can I

a. make certain i have access to the commercial rep
b. find the right command to install realplayer from that repo

(I think people are mostly debating different ways to do b. on this forum)

---

### Post by zvacet on 2008-01-03
1.To be sure that you can use partner repo,after adding it to your source list and saving and closeing file run 

```
sudo apt-get update
```

2.It look like that program is not in partner (not for Gutsy)


Try to follow **oldos2er** advice

---

### Post by arnicainthemembrane on 2008-01-03
got it. thanks. as usual this process of asking dumb questions and following false leads has helped me understand this OS better.

---

