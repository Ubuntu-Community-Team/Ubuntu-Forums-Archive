---
title: "Upgrade question"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by JReagan1990 on 2006-07-29
I have been playing around with ubuntu for a bit, and noticed all the repositories checked for updates while using the update manager.  When the new release arrives (edgy eft), will the update manager update my computer, or will I need to find an"updated repository"?  Thanks in advance!:D

---

### Post by K.Mandla on 2006-07-29
If I understand you correctly, your machine will stick to Dapper unless you tell it otherwise.

Whenever Edgy is released (or I should say, in October when Edgy is released), your system will stay Dapper until you tell it to make the jump to Edgy.

If you're feeling adventurous, you can do that now by opening your sources file with

```
sudo nano /etc/apt/sources.list
```
and replacing every word *dapper* with *edgy*. Then 

```
sudo apt-get update
```
and

```
sudo apt-get dist-upgrade
```
However, I wouldn't recommend it. It's still very early in Edgy's development, and the potential for things to break is pretty high. 

I hope that answered your question! :)

---

### Post by JReagan1990 on 2006-07-30
Thanks!  That answers my question perfectly!:D

---

### Post by Ramses de Norre on 2006-08-23
Actually you'll want to use aptitude instead of apt-get.. And be sure to expect breakage (I'm typing this from command line because my X server just broke..)

---

