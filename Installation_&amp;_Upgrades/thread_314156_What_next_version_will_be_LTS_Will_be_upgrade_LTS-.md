---
title: "What next version will be LTS? Will be upgrade LTS-&gt;LTS"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by artik on 2006-12-07
Hello,
I do not really like Edgy and I still work with dapper.

The problem is what will happen when I'll want to upgrade for example to 7.10? I'll have to do all the stages?

6.06->6.10->7.04->7.10

I was told that the "skip" upgrade is not supported.


What happens with upgrade from LTS to LTS will it be possible?
When next high quality LTS version will be released?

Is there any answers on these questions?

---

### Post by az on 2006-12-07
> **artik said:**
> 
What happens with upgrade from LTS to LTS will it be possible?
When next high quality LTS version will be released?


Not only will it be possible, but it will be easy.  The graphical updates-notifier showed a message and an easy click-to-upgrade box in Breezy when Dapper was released.  It will show up again when the next LTS is released.

The only reason it was not shown when Edgy came out is because Edgy is not an LTS.

---

### Post by artik on 2006-12-07
1st - upgade is not so easy as it looks like... But

Ok there are several issues that I do not like:

1. Official site tells that you cannot skip upgrade
2. I do not know the release shuelder of the LTS

So if I remain with dapper I do not know how much time will I be stuck with it and if I will be able to upgrade at all.

These are important issues.
Artik

---

### Post by Hendrixski on 2006-12-07
Dapper is going to be supported for x number of years, so if you never want to upgrade, feel free to stay with it.  From what I understand, the major changes in Debian-based distro's (like Ubuntu) is the change in the apt packages being used, and updating your software to contain the latest releases of your software from your new apt repository... plus a few harder things deep in the bowels of the operating system, like maybe a kernel update (which is great but I'm not convinced you NEED to have the latest greatest kernel).

Also, just because it's not "supported", doesn't mean that nobody has written a way to do it. It just means Ubuntu won't be the one to give you the script.  There are many software that are not "supported" but work perfectly well.

---

### Post by az on 2006-12-07
> **artik said:**
> 1st - upgade is not so easy as it looks like... But

The update-manager is supposed to iron out the majority of dist-upgrading glitches.  

> **artik said:**
> 

Ok there are several issues that I do not like:

1. Official site tells that you cannot skip upgrade

Where does it say that?  It is a fact that upgrading from one LTS to the next is going to be supported.  

> **artik said:**
> 
2. I do not know the release shuelder of the LTS

Neither does anyone else.  When a release seems like it can be exceptional, it will be an LTS.  I can probably imagine that the next LTS will happen before Dapper is no longer suppported - which is in two and a half more yeards on the desktop.

> **artik said:**
> 

So if I remain with dapper I do not know how much time will I be stuck with it and if I will be able to upgrade at all.


You *will* be able to upgrade from it to the next LTS.  No one running Ubuntu on a production workstation is going to want to run Edgy or Feisty.  But they will want the next LTS release.

---

### Post by Qew on 2006-12-07
> **azz said:**
> Not only will it be possible, but it will be easy.  The graphical updates-notifier showed a message and an easy click-to-upgrade box in Breezy when Dapper was released.  It will show up again when the next LTS is released.

The only reason it was not shown when Edgy came out is because Edgy is not an LTS.

Is there any reason why my Xubuntu Dapper Update Manager has the words "New distribution release '6.10' is available" with a nice upgrade button next to it?

However, yeah, I'm sticking with Dapper for a while myself and hope that an upgrade to the next LTS is available.

---

### Post by az on 2006-12-07
> **Qew said:**
> Is there any reason why my Xubuntu Dapper Update Manager has the words "New distribution release '6.10' is available" with a nice upgrade button next to it?


I dunno.  That is not so in Ubuntu.  In Ubuntu, you have to run the update manager by hand to get the upgrade option (update-manager -c). It is not offered otherwise.

---

