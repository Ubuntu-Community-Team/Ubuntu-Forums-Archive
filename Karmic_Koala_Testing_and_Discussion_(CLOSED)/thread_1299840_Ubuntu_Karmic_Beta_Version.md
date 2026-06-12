---
title: "Ubuntu Karmic Beta Version"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by arepaking on 2009-10-24
Hi all,
Pardon my ignorance please, but if I install Karmic Beta Version will it update to the final version once this one is release?

Or, once the final version is released it would be better if I do a fresh new installation?

Thanks in advance,
AK

---

### Post by howefield on 2009-10-24
> **arepaking said:**
> but if I install Karmic Beta Version will it update to the final version once this one is release?

Keep updating and you will have the final release.

---

### Post by arepaking on 2009-10-24
How can you tell if you have the beta or you system got updated to the final version?

Thanks though for your quick response.

---

### Post by ikisham on 2009-10-24
Now it's not even beta anymore, it's release candidate. That means it's almost ready for final (expected for next thursday).

If you install the updates, by thursday (29/10) you'll have a system like the final. It's just like normal updates, it get's better and better.

Understand? There's no difference, it's the same Karmic, only you can install a few days earlier, if you like.

---

### Post by arepaking on 2009-10-24
Thanks Ikisham,
Now, between upgrading to karmic release candidate and doing a fresh install... what would you guys recommend?

---

### Post by flipper9 on 2009-10-24
I'd recommend doing a fresh install this time around.

Why?  You can't get the new disk format EXT4 without doing a fresh install (same thing with Grub2).  Yes; you can "upgrade" your EXT3 --> EXT4, but the disk structure won't get upgraded and you won't benefit from the speed enhancements.

---

### Post by arepaking on 2009-10-24
I'm using EXT4 since 9.04 so I guess this is not my concern. Now I don't know if I am using GRUB2. Is there a way to check this?

---

### Post by ikisham on 2009-10-25
> **arepaking said:**
> Thanks Ikisham,
Now, between upgrading to karmic release candidate and doing a fresh install... what would you guys recommend?

You decide. Just for you to know, I've never upgraded myself (this has Karmic installed from beta and updated to its current state and there's Hardy in another pc).
If you have your system all set-up (and if you haven't installed things from source or have PPA's enabled) I think you should upgrade. Upgrade is meant to work like a normal update, only you'll get the newer version.

If it doesn't go well, then you can do a fresh install if you like.

I always keep my data in a different partition from the system so it's safe from any system misoperation.
Actually I tried to upgrade once from a Crunchbang (Jaunty based) install to Karmic beta and it didn't go well, but then I had a few PPA's enabled that certainly didn't make things simpler (and I changed the sources.list by hand if I remember well, so it isn't a reliable example).

As for GRUB, the upgrade won't change it for GRUB 2 but you can install it afterwards if you want.

---

