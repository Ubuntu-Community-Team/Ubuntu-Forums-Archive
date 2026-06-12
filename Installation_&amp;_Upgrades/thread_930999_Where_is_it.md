---
title: "Where is it ????"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by dgoddard1 on 2008-09-26
I don't like "Evolution Mail" So I downloaded the thunderbird deb file and installed it.   

It said it _re_-installed it successfully but it did not tell me where and I can't find it.  It certainly is not in my application list.

1. Where am I supposed to look for newly installed sofware applications
2. Where should I look for thunderbird
3. How do I put it in my applications menu drop down list?  

Obviously I am new to Ubuntu.  I am also frustrated by the lack of specificity in information

I am also confused by why my attempts at spell checking this post keep coming up with suggested German spellings

---

### Post by JC Cheloven on 2008-09-26
Please try this at a terminal ```
thunderbird %u
``` If Thunderbird is installed, this command should bring it up.

If that works, it is not difficult to add a menu item. Just navigate to system -> preferences -> main menu (sorry, not sure about the exact words, 'cause I'm running a localized ubuntu) and probably you'll find your way around. If not, don't hesitate to come back here to ask :-) 

By the way: Did you uninstalled evolution prior to installing thunderbird? It should be a good idea: I think evolution tightly integrates in the ubuntu desktop; perhaps too tightly ;-)

EDIT: as for your question about the installed programs: most of the programs you install go to /usr/bin. Also, if you install via synaptic, aptitude or apt-get, a copy of the .deb file is saved in /var/cache/apt, which can be useful if you need reinstalling (either on the same or onto a different pc).

---

### Post by steveneddy on 2008-09-26
> **JC Cheloven said:**
> Please try this at a terminal ```
thunderbird %u
``` If Thunderbird is installed, this command should bring it up.

If that works, it is not difficult to add a menu item. Just navigate to system -> preferences -> main menu (sorry, not sure about the exact words, 'cause I'm running a localized ubuntu) and probably you'll find your way around. If not, don't hesitate to come back here to ask :-) 

By the way: Did you uninstalled evolution prior to installing thunderbird? It should be a good idea: I think evolution tightly integrates in the ubuntu desktop; perhaps too tightly ;-)

I don't think it is necessary to uninstall Evolution.

If you don't find Thunderbird in the above way try in terminal:

```
locate thunderbird
```

---

### Post by cariboo on 2008-09-27
I don't suppose you checked Applications-->Internet-->Mozilla Thunderbird Mail/News ?

Jim

---

