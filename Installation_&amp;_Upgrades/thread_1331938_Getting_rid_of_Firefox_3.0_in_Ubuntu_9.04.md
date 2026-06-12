---
title: "Getting rid of Firefox 3.0 in Ubuntu 9.04"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by giyad on 2009-11-19
I've just installed Firefox 3.5 via 
```
sudo apt-get firefox-3.5
```
but now I have Firefox 3.0 and 3.5.  I want to completely get rid of 3.0 but there are a bunch of 3.0's in the repositories and I just don't know whats safe to get rid of and whats not.  Can someone help me out?

I've attached a screenshot.  Also, the first thing in the list is just simply firefox, should i get rid of that? It says 3.0.15 in the info, should I just get rid of anything htat has that version in the info???

---

### Post by wojox on 2009-11-19
It's actually recommended to leave both versions for dependency issues. You could try marking all firefox 3.0 packages and removing them. Just watch what it tries to pull out with it.

---

### Post by giyad on 2009-11-19
> **wojox said:**
> It's actually recommended to leave both versions for dependency issues. You could try marking all firefox 3.0 packages and removing them. Just watch what it tries to pull out with it.
seems kind of redundant though to have both...

I decided to remove everything but I made sure to keep "ubufox"

So far so good

---

