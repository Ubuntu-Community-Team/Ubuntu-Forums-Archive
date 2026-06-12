---
title: "Generic Kernel"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2006-11-29
I'm sure this has been mentioned somewhere, but my search skills must be lacking because I'm not finding it.

I just upgraded my Ubuntu install and I installed from scratch my Kubuntu install (upgrading did not work at all).  Ubuntu uses a similar kernel to what I had with 386 at the end of the kernal name.  But, Kubuntu uses a kernel with generic at the end.

Why the difference (I'm guessing upgrade vs install) and from a user standpoint, is there a difference?

Thanks,

Steve

---

### Post by az on 2006-11-29
> **SteveF said:**
> I'm sure this has been mentioned somewhere, but my search skills must be lacking because I'm not finding it.

I just upgraded my Ubuntu install and I installed from scratch my Kubuntu install (upgrading did not work at all).  Ubuntu uses a similar kernel to what I had with 386 at the end of the kernal name.  But, Kubuntu uses a kernel with generic at the end.

Why the difference (I'm guessing upgrade vs install) and from a user standpoint, is there a difference?

Thanks,

Steve

Dapper uses a generic kernel named 386 and a few optimized kernels (686, k7, etc..)  In Edgy, those optimizations are done at run time instead of compile time.  You should be able to install the linux-generic kernel on your Dapper box which is upgraded to Edgy.

---

### Post by SteveF on 2006-11-29
> **azz said:**
> Dapper uses a generic kernel named 386 and a few optimized kernels (686, k7, etc..)  In Edgy, those optimizations are done at run time instead of compile time.  You should be able to install the linux-generic kernel on your Dapper box which is upgraded to Edgy.
So are you saying the generic will potentially be a better fit to my upgraded box than the existing 386 kernel because my processor is most likely better than a 386?

Steve

---

### Post by az on 2006-11-29
> **SteveF said:**
> So are you saying the generic will potentially be a better fit to my upgraded box than the existing 386 kernel because my processor is most likely better than a 386?

Steve

I don't know.  It depends.

What has happened is that the default kernel you get with an Edgy install is called linux-generic when it used to be called linux-386.  

There is an up-to-date linux-386 kernel in Edgy too, which means that you will still be up-to-date if you stick with the 286 kernel that you got from Dapper.  I seem to remember the discussion about this that said that the 386 kernel has been able to do those optimisations for a while now.  I don't really know what the difference is between the two in Edgy.

---

