---
title: "Multiple Problems/Questions"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by CyberCod on 2006-08-29
I'm installing Ubuntu on a friend's PC, I've already got it on my machine running fine, but different hardware = different problems.](*,) 

My first woe is that the processor is not recognized.  Its 2Ghz Celeron-D and  the device manager shows unknown processor and the system is as sluggish as a salted snail.  Is there a way to re-run the hardware configuration? or manually define the processor?  If I can manually define it, does anyone have a link to what settings I should use?

2nd question for my general info, is it possible for two linux installations to share the same swap partition?

I'm sure I've got more questions, but they're escaping me right now.

---

### Post by Jagot on 2006-08-29
1.
Try installing the 686 kernel:

```
sudo aptitude update
sudo aptitude install linux-686
```

2.
Yes.

---

### Post by CyberCod on 2006-08-29
if the 686 kernel isn't right, how do I change it back? and will it still boot up if it isn't right?

---

### Post by Jagot on 2006-08-29
The old kernel will appear in your GRUB menu when you boot.  Just select the old kernel if 686 does not work.  686 is certainly the correct kernel for your processor though.

---

### Post by CyberCod on 2006-08-29
Thanx for the quick replies.

I remembered the other question.

Is there any tried and true methods for getting TV-out to work for Radeon 7000VE ?  I'm seeing several methods via google, but don't know which route to go.

---

