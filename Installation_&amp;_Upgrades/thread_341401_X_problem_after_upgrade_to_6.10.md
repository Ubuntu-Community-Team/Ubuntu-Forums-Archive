---
title: "X problem after upgrade to 6.10"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by psychoviking on 2007-01-18
Hello, I have just checked on my ubuntu machine after upgrading to 6.10 and I have a problem.  When it boots x tries to start, I see the circular cursor on a black background then the screen goes a light brown colour.  It alternates between this 'ubuntu brown' and black a few times then settles on the brown colour and nothing else.  Any ideas what I can do?  I have nearly pulled the remainder of my hair out.  TIA

---

### Post by taurus on 2007-01-18
Boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by psychoviking on 2007-01-18
I have lilo on my machine and can't figure out how to get a command prompt.  Once x tries to start ctrl/alt/f2 doesn't work.  Any ideas?

---

### Post by psychoviking on 2007-01-18
Somehow I managed to get a command prompt, tried the command suggested but couldn't do startx so restarted.  Same problem but the cursor now looks slightly larger.  Help!

---

### Post by dowbjts on 2007-01-18
what does the "-phigh" setting do in the reconfig??

---

