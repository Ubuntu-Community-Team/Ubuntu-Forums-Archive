---
title: "Upgrade from 64bit to 32bit?"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by doobiest on 2010-03-22
Hi,

Short of the story is I have an AMD64bit system for my 'server'.  I find that there is lacking package support for ubuntu 64bit.  Some apps I want to install work fine on 32bit ubuntu but not in 64bit ubuntu. More importantly the 64bit package for my ati drivers don't work, however they do on a 32bit version of ubuntu.  

It would make sense to do a fresh install of ubuntu 32bit to avoid problems like this in the future. However my server has been running for years.. since ubuntu6. And it is highly customized. It would take too long to configure my server from scratch, I really want to avoid that.

So I'm wondering, next time I do a dist upgrade.. say from 9.10 to 10.04. Is there a way I could trick the update manager in to upgrading to 32bit packages/kernel etc?

---

### Post by zvacet on 2010-03-23
I don´t think you can trick update manager.All your customization should be in home directory and I believe on server you have separate home.That is all I can think of right now.Maybe someone with more experienced will give you better advice.

---

### Post by Slim Odds on 2010-03-23
> **zvacet said:**
> I don´t think you can trick update manager.All your customization should be in home directory and I believe on server you have separate home.That is all I can think of right now.Maybe someone with more experienced will give you better advice.

On a server there would a many customizations in the /etc (at least).

Unfortunately the 32 bit world and the 64 world are worlds apart. ;)

---

