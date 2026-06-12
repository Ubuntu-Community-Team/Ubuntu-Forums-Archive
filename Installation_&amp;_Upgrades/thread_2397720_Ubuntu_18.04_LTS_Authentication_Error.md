---
title: "Ubuntu 18.04 LTS Authentication Error"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by Tomfilery on 2018-08-02
I've just upgraded my Lenovo laptop from 16.04.LTS to 18.04 LTS and now can't get into Ubuntu (dual loading with Win10 is OK).
When I get to the login screen, my user id appears, but if I then click on it I get a flash of the next screen (presumably where I'd enter my password) and "Authentication Error" appears and the system hangs - it shows the last block check data.

I can't see how to access my files, or get into terminal to investigate further. 

Would appreciate help please.

Regards tomfilery

---

### Post by cmcanulty on 2018-08-02
[COLOR="#FF0000"]use at your own risk[/COLOR]
, but command below and a restart fixed a similar problem for me, use recovery mode at boot and then pick drop to root shell prompt

```
sudo apt remove upstart --purge
```

---

### Post by Tomfilery on 2018-08-05
cmcanulty,

Thanks - in desperation I tried your suggestion, with no noticable effect.

Looks like my Ubuntu is completely screwed.

Regards tomfilery

---

### Post by Sleepy-zz-John on 2019-03-01
Hmmm... interesting!    I encountered exactly the same error only a week ago and posted looking for a way of logging in. 

The problem I have with cmcanuly"s  suggestion last August is that it comes up with ```
 30: Read-only file system 
``` and ```
 --set solutions returned error code 2
```

   +   John

---

