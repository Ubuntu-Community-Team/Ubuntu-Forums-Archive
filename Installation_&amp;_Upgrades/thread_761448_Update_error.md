---
title: "Update error"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by bcsco on 2008-04-21
I had two updates waiting when I arrived at my desktop this morning. During the update my PC froze completely. I had to pull the plug and restart. Now, when I try to finish the update (the second file(apt-utils) I get the following error message:

[I]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/I]

Exactly how am I to respond to this so I can get my update manager working again? I'm new to Ubuntu and don't understand a lot about Terminal and how it works. I need someone to walk me through this.

Thanks in advance for any help that can be given.

BCSCO

---

### Post by Partyboi2 on 2008-04-21
Open a terminal (Applications>Accessories>Terminal)
then type or paste
```
sudo dpkg --configure -a
```

---

### Post by bcsco on 2008-04-21
That did it. Thanks much for your help. Terminal and its commands is one area that's really hard to understand for me.

---

