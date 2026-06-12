---
title: "Edgy to Feisty upgrade &gt; now XGL garbled."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by SwordRaven on 2007-04-19
Ok, strangeness.

Before I upgraded to Feisty, GNOME wouldn't boot anymore, it crashed while loading something that I could never track down, so I exclusively used my XGL/Beryl session instead. Which was fine by me.

But now when I boot XGL it is garbled and totally unusable. However, GNOME is running sweet as a nut again.

Any ideas? I haven't done anything outside of what the upgrade tool asked me to do.

Cheers.

---

### Post by smartalecks on 2007-04-19
Upgrading with a custom Xorg configs or a composite manager is usually not a good idea :/. Erm... you could try doing a clean install (probably what you should've done from the first place) after backing everything up (if you really want beryl, this might be easiest) and reinstalling beryl. 

But first! What sort of garbling are you getting from your XGL/Beryl session?

---

### Post by SwordRaven on 2007-04-19
> **smartalecks said:**
> Upgrading with a custom Xorg configs or a composite manager is usually not a good idea :/. Erm... you could try doing a clean install (probably what you should've done from the first place) after backing everything up (if you really want beryl, this might be easiest) and reinstalling beryl. 

But first! What sort of garbling are you getting from your XGL/Beryl session?

[http://i67.photobucket.com/albums/h283/SwordRaven/Screenshot.png](http://i67.photobucket.com/albums/h283/SwordRaven/Screenshot.png)

It looks like that :)

I've just noticed the resolution that the picture was taken at... ok that might offer an explanation.

Now, how to set my XGL resolution back to what it was? 1280x1024

"Composite Manager" means very little to me, it's just something I blindly did as a step towards getting Beryl :(

---

### Post by SwordRaven on 2007-04-19
Bump.

Any info appreciated.

---

### Post by jordanmthomas on 2007-04-19
Not sure what you need to do (aside from editing your xorg.conf the same way you did before) but I believe your screenshot is in 1280x1024, but was scaled down by imageshack.  Although the image itself is 800x640 the resolution looks a lot higher.

---

### Post by SwordRaven on 2007-04-19
> **jordanmthomas said:**
> Not sure what you need to do (aside from editing your xorg.conf the same way you did before) but I believe your screenshot is in 1280x1024, but was scaled down by imageshack.  Although the image itself is 800x640 the resolution looks a lot higher.

xorg.conf hasn't changed at all. That's why I'm superconfused.

How do I remove and reinstall XGL/beryl?

I spent such an enormous amount of time getting fglrx to work that I have forgotten how xgl was installed (repository? compiled? shell script?)

---

### Post by SwordRaven on 2007-04-19
Any more ideas?

---

### Post by blkdimnd on 2007-04-21
I'm having the same problem.  But no ideas on how to fix it.

---

