---
title: "correct procedures for upgrade UbuntuStudio 16.04 to UbuntuStudio 18.04"
date: 2019-07-11
forum: Installation &amp; Upgrades
---

### Post by de Bacon on 2019-07-11
I always try searching for answers, though 99% of the time I find no answers suitable.  I believe brain to vocabulary is the issue.  I am not a techie kind of person.  Even so, I have only used l ubuntu flavor x since 2009.  I can use the command line for simple things (sometimes) if I understand the proper sequence for a given process/procedure.

Anyhow, I want to upgrade Ubuntu Studio 16.04 to Ubuntu Studio 18.04 but I find nothing specific to Ubuntu Studio.  I find instruction for Ubuntu generic but nothing for Ubuntu Studio.  I don't know that these instructions are or are not compatible with Ubuntu Studio, as they are not the same, to my understanding.   

Thanks in advance.  I hope there is a simple answer and list available for this.  I can't find it if there is.

Tom

---

### Post by CatKiller on 2019-07-11
The instructions are still applicable.

All the Ubuntu flavours use the same repositories with the same software in. Where they differ is in default configurations: the main ones in Ubuntu Studio's case are Xfce, low-latency kernel by default, their own theming, different default applications.

Note that the Studio-specific parts are not Long Term Support for 18.04: they're a small volunteer project and don't feel that they have the manpower to offer Long Term Support at this time, so they won't do point releases like the other flavours can.

In terms of the upgrade path it makes absolutely no difference whether you're using Ubuntu Studio or you've simply installed the low-latency kernel in standard Ubuntu, say. It's all the same stuff from the same place.

---

### Post by de Bacon on 2019-07-11
Thank you.  That which you stated was quite helpful to me, removing a long time question as to upgrading.  

I believe I am on my way to phase next, 18.04.  I looked at my repository list in synaptic, then thought to click the upgrade release notice, which delivered its own path to upgrading.

---

