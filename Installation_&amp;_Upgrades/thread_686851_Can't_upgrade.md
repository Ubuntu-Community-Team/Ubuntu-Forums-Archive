---
title: "Can't upgrade"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by happysmileman on 2008-02-03
I've just installed Kubuntu 7.10, and there was 130 upgrades available... It installed 14 of them, then quit with an error, so i tried again, now every time I try to do an update, it fails on updating the kernel, the output is as follows.

```
*** stack smashing detected ***: /usr/bin/perl terminated
Segmentation faul (core dumped)
Setting up tzdata (2007k-0ubuntu0.7.10) ...
*** stack smashing detected ***: /usr/bin/perl terminated
dpkg: error processing tzdata (--configure):
  subprocess post-installation script killed by signal (Segmentation fault), core dumped
Errors were encountered while processing:
 tzdata
```

Then it tells me a new distribution update is available and asks me to update... If I click update it says it will now update to 7.10... Which of course it is already updated to.

---

### Post by Partyboi2 on 2008-02-03
If you haven't already try from a terminal
```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by happysmileman on 2008-02-03
> **Partyboi2 said:**
> If you haven't already try from a terminal
```
sudo apt-get update
``````
sudo apt-get upgrade
```


Yeah just tried that, it works... Now I'll have to see if it happens again next time updates are available, or whether updates fixed it

---

### Post by Partyboi2 on 2008-02-04
from what I read its a problem with adept. So if you ever have problems with adept try using the terminal. :)

---

