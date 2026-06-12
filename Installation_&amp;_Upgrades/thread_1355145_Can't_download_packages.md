---
title: "Can't download packages"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Pidron on 2009-12-14
Hi guys, I am running Karmic and experience the following problem:
everytime I try to install a new package with Ubuntu Software Centre or Synaptic, the download gets stuck a few seconds after the start, until I get the "unable to fetch..." message. I have tried already to change the server from the Software Source but no joy...
Any idea?
Thanks a zillion!

---

### Post by zvacet on 2009-12-15
System>admin>software sources>check all under ubuntu software (except source) and first two under updates tab.Reload.Try to install packages again.

---

### Post by xifer on 2009-12-15
> **Pidron said:**
> Hi guys, I am running Karmic and experience the following problem:
everytime I try to install a new package with Ubuntu Software Centre or Synaptic, the download gets stuck a few seconds after the start, until I get the "unable to fetch..." message. I have tried already to change the server from the Software Source but no joy...
Any idea?
Thanks a zillion!

Is this a wireless connection?  Can you try to update using a wired connection?

---

### Post by Pidron on 2009-12-16
I tried with zvacet's suggestion but no joy.
I am using a wired connection.
Funny thing is I can surf the web no probs, but when it comes to downloading packages it gets stuck nearly immediately. I have tried selecting different servers but there's no difference. Could it be a problem with my internet provider?

---

### Post by slakkie on 2009-12-16
Could you show us the output of;

aptitude update

---

### Post by Pidron on 2009-12-16
Here it is:
Writing extended state information... Fatto
6% [Connessione a ubuntu.ictvalleumbra.it (1.0.0.0)] [Connessione a archive.canonical.com (1.0.0.0)] [Connessione a pa6% [Connessione a ubuntu.ictvalleumbra.it (1.0.0.0)] [Connessione a archive.canonical.com (1.0.0.0)] [Connessione a packages.medibuntu.org 6% [Connessione a ubuntu.ictvalleumbra.it (1.0.0.0)] [Connessione a archive.canonical.com (1.0.0

Looks as if it gets stuck at 6%. And this happens with any server (might get stuck at 3% for instance).

---

### Post by slakkie on 2009-12-16
Looks like your using some kind of proxy.

---

### Post by Pidron on 2010-02-24
Found out what the problem was: IPV6 was disabled.
I enabled it and now it works fine.:)

---

