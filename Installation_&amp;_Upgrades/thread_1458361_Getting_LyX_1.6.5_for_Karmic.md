---
title: "Getting LyX 1.6.5 for Karmic"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by protargol on 2010-04-19
I'm trying to figure out how to get the newest build for LyX properly (ie not from building it myself) for Karmic.  I do ```
sudo apt-get upgrade lyx
```, but it doesn't pick up the 1.6.5 (although it looks like it is prepared to ship out with Lucid.  Any ideas on how to get it to just work?

It's these minor problems with Ubuntu being slow to upgrade to the newest builds of software (ie Firefox 3.6) that makes it a little bit frustrating.  Maybe I should learn to program so I can help out more...:)

---

### Post by rhino9191 on 2010-04-19
Hey im not sure if this will work but give this code a try this is how i alway get the latest OOo
```
sudo add-apt-repository ppa:lyx-pkgs/ppa
```
Then update.

---

### Post by mdebusk on 2010-04-20
> **rhino9191 said:**
> Hey im not sure if this will work but give this code a try this is how i alway get the latest OOo
```
sudo add-apt-repository ppa:lyx-pkgs/ppa
```
Then update.

The ppa is ppa:lyx/ppa. [See launchpad]("https://launchpad.net/~lyx/+archive/ppa").

Be careful what you add to your package manager.

---

