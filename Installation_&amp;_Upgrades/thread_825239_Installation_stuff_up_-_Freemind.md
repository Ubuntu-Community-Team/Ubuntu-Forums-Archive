---
title: "Installation stuff up - Freemind"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by Lorna on 2008-06-10
When I try to open synaptic package manager i get this error:

E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Synaptic will not load and i have no idea what i have done.  I was trying to load Freemind and think i did something wrong.  Can anyone suggest an easy fix please.  i am a newbie so will need simple instructions, Ta,

Lorna

---

### Post by Partyboi2 on 2008-06-11
try opening a terminal (Applications>Accessories>Terminal)and typing

```
 sudo dpkg --configure -a 
``` If that does not work then you could try
```
 sudo dpkg -r --force-remove-reinstreq sun-java5-bin
```

---

### Post by Lorna on 2008-06-15
Thanks it worked you rock and i love your pic!

---

