---
title: "upgrade to 10.04"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by xtracool_protik on 2010-03-30
Hey guys,
 I've been using Ubuntu for nearly 2 years now and I'm getting good at it everyday, Now with 10.04 just around the corner soon I'll be upgrading to Lucid from karmic but thats where I've a bit of a issue.
 However everytime I upgrade my distribution I need to update my ppa by myself is there a way to update keys and ppa automatically with upgrade? or before/after upgrade?
 Last time I tried exporting my package info from synaptic but I simply don't know how does that work coz when I tried importing it on another machine it gave me an error.
 Well I can always note down all my repositories and add them after upgrade by myself, but its just pain to do that.
 Thanks for help :) I'll be looking forward to this upgrade especially for gnome 3.0 and if compiz is tied with it :D

---

### Post by xtracool_protik on 2010-04-01
bump

---

### Post by khelben1979 on 2010-04-01
> **xtracool_protik said:**
> Well I can always note down all my repositories and add them after upgrade by myself, but its just pain to do that.

Why would it be a pain? Make a backup of the of /etc/apt/sources.list and use the search and replace option from a text editor if you need to do some changes to it.

---

### Post by UCSBGauchosRock on 2010-04-01
> **xtracool_protik said:**
> Hey guys,
 I've been using Ubuntu for nearly 2 years now and I'm getting good at it everyday, Now with 10.04 just around the corner soon I'll be upgrading to Lucid from karmic but thats where I've a bit of a issue.
 However everytime I upgrade my distribution I need to update my ppa by myself is there a way to update keys and ppa automatically with upgrade? or before/after upgrade?
 Last time I tried exporting my package info from synaptic but I simply don't know how does that work coz when I tried importing it on another machine it gave me an error.
 Well I can always note down all my repositories and add them after upgrade by myself, but its just pain to do that.
 Thanks for help :) I'll be looking forward to this upgrade especially for gnome 3.0 and if compiz is tied with it :D

You do not need to upgrade your repositories, they upgrade to the lucid ones, if available, on their own. As for repositories with Launchpad, sticking with the karmic repo's you should be fine.

---

### Post by uRock on 2010-04-01
> **khelben1979 said:**
> Why would it be a pain? Make a backup of the of /etc/apt/sources.list and use the search and replace option from a text editor if you need to do some changes to it.

+1 this method should work fine.

---

### Post by xtracool_protik on 2010-04-01
Hey thanks guys,
 I didn't know I can just use Karmic repos (launchpad or any third party) with Lucid without any changes. So does it mean even if the third party vendor doesn't provide any repo for Lucid, I'll be just fine with Karmic's?
 Thanks again guys taking backup of sources sounds good. However when I put it back in place (probably after replacing "Karmic main" to "Lucid main" etc.), won't I need to import keys?

 And I assume taking backup of sources works even for formatting my OS and reinstalling, in that case:
 1. How about keys?
 2. Can I somehow save my package selection?

 Thanks

---

