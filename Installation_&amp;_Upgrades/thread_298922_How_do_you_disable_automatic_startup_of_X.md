---
title: "How do you disable automatic startup of X ?"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by emersony on 2006-11-13
I have breezy installed on my laptop and of course it boots into X windows. But I hardly ever use X, just one of the TTY's. 

So what I would like is for it to always boot to the command line, and then if I want to start X I just type startx. 

What is the easiest way to affect this change?

Also I would like to remove the cups daemon since I have no need for it on my laptop. 

Can someone tell me how to do this?

thanks, 

Emerson

---

### Post by taurus on 2006-11-13
```
sudo aptitude remve cupsd
```
And for X, try removing gdm...

```
sudo aptitude remove gdm
```

---

