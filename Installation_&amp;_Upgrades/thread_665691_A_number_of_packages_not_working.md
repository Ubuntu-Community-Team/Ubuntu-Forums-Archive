---
title: "A number of packages not working"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Jonzo82 on 2008-01-12
Hi there,

I've recently installed Ubuntu because of it's "it just works" reputation. Turns out it doesn't... there are a number of third party packages that don't seem to work properly, and according to bug reports they have been broken for months?!

Packages I have installed, that don't work properly, have fixes, but just haven't had the fixes released:

flashplugin-nonfree
google notifier
Tilda

I'm not really that upset, ubuntu doesn't run these projects after all, but apparently they all have fixes in "repository versions" that have been submitted as patches, and yet they've been broken for months...

Is this normal for Linux distros?

---

### Post by Crenfinkle on 2008-01-12
I've tried not to grow too attached to official packages in the repos for reasons similar to this. *Most* of them work flawlessly, but some times there will be problems. In cases like this I get the software I want from upstream (from the actual providers) and install it manually.

Also, the packages in the repos are often quite old and don't have all of the functionality included in newer versions. Be careful with this approach, but as long as you install binaries for your architecture or understand the software you're installing you should be ok. I hope a few sketchy packages don't take away your enthusiasm for ubuntu, which is one of the best distros I've ever used!

---

### Post by Jonzo82 on 2008-01-13
Yeah I've tried redhat and debian before and I've got to say that Ubuntu has been by far the friendliest! Although I didn't know about the packaging system in debian so maybe I shouldn't bag it.

I've seen a lot of recommendations against avoiding the package system because it isn't updated in the same way, so I guess I was a little wary of compiling my own stuff from source... also there's package dependencies, and errors and all sorts, like a whole new world! haha.

I think the package system has so much potential if it was updated a lot more and bug fixes were released quicker. Guess I'll just have to deal with it ;-)

---

### Post by zvacet on 2008-01-13
> there are a number of third party packages that don't seem to work properly, and according to bug reports they have been broken for months?!


Yes,that is why they are third party.They are not responsibility of Ubuntu developers,because they are not official Ubuntu packages.For flashplugin-nonfree try 

```
sudo apt-get install ubuntu-restricted-extras
```

that way you will get flash,Java...

---

### Post by Jonzo82 on 2008-01-13
ok thanks :-) i'll give that a go.

---

