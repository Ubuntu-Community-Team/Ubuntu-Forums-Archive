---
title: "Simple Update Error"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by dothedorky on 2007-01-16
Hello all. I was about to configure evolution for the first time, and figured i'd update my system before all that.

I did 

```
sudo apt-get update
```

and all seemed to go well until the end where it states

```
Reading package lists... Done
W: GPG error: http://debian.space-based.de experimental Release: The following s ignatures couldn't be verified because the public key is not available: NO_PUBKEY EB020D4677AFC5B7
W: You may want to run apt-get update to correct these problems

```

and  i can run apt-get update several times and still get the same error.

Any ideas?

---

### Post by taurus on 2007-01-16
Edit /etc/apt/sources.list and place a # in front of that line to comment it out.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by dothedorky on 2007-01-16
ahh, this worked wonderfully! thankyou!

---

