---
title: "Problems installing updates through Synaptic PM"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by Unicast on 2006-02-23
Whenever ubuntu tells me there are updates available I go into Software Updates where the available updates are listed. However when I click on "Install" the download window opens and closes within the blink of an eye! What the hell is going on?

This is the contents of my sources.list file:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

Any help would be gratefully appreciated. :mrgreen:

---

### Post by aysiu on 2006-02-23
Do you run into the same problem when you try to update from the command-line? ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Unicast on 2006-02-23
I have tried updating via the comand line in the past, and I've had problems connecting to ftp.free.fr - it normally just times out.

However this evening after multiple attempts I have been able to update via Synaptic Package Manager. Is this a problem with ftp.free.fr being overloaded with download requests? If so would I be better using a mirror? And if so which mirror would you recommend?

---

