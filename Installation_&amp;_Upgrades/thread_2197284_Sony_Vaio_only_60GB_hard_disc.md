---
title: "Sony Vaio only 60GB hard disc"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by Timmoore001 on 2014-01-03
Old Sony Laptop.

I've tried 32 bit 13 and 12.04 both lockup during the downloading of the language packs...

I've no idea what to do next.

Any thoughts anyone ?

A very puzzled,

Tim

---

### Post by Bucky Ball on 2014-01-03
More information, please. Can you try Ubuntu from the installation media and get to a desktop but it won't install?

What are the specs of your computer (you say old, but no RAM or CPU specs)?

---

### Post by Bucky Ball on 2014-01-03
More information, please. Can you try Ubuntu from the installation media and get to a desktop but it won't install?

What are the specs of your computer (you say old, but no RAM or CPU specs)?

---

### Post by Timmoore001 on 2014-01-03
it was installing everything ok until it got the language packs then it froze.

Since my first post I overcame some of the problem by unplugging the internet link before installation and all is well apart from the third party mp3 drivers etc..

Any thoughts on getting the drivers ?

Many thanks for responding.

:  )))

Tim

---

### Post by plucky on 2014-01-03
> **Timmoore001 said:**
> it was installing everything ok until it got the language packs then it froze.

Since my first post I overcame some of the problem by unplugging the internet link before installation and all is well apart from the third party mp3 drivers etc..

Any thoughts on getting the drivers ?

Many thanks for responding.

:  )))

Tim

Do you have an internet connection?

If yes

Open a terminal (CTRL+ALT+t) and run ```
sudo apt-get update && sudo apt-get upgrade
```

and also ```
sudo apt-get install ubuntu-restricted-extras
```

Post the results if any errors shown.

Good Luck

---

