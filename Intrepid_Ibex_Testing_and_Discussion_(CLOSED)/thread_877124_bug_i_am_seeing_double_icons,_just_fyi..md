---
title: "bug: i am seeing double icons, just fyi."
date: 2008-08-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2008-08-01
bug: i am seeing double icons 4 the same device, just fyi.

see attachment.

---

### Post by kevpan815 on 2008-08-01
this issue currently affects ubuntu 8.10, just fyi.

---

### Post by ronacc on 2008-08-01
known issue already reported as bug#251991

---

### Post by kevpan815 on 2008-08-01
> **ronacc said:**
> known issue already reported as bug#251991

Thanks 4 letting me know about that.

---

### Post by Gina on 2008-08-01
Yes, we're all seeing double!

---

### Post by OutOfReach on 2008-08-01
I too have this, and it gets kinda annoying when I have to unmount the drive, I have to pick the right one or else it won't unmount. :P

---

### Post by aamukahvi on 2008-08-01
The bug also says it's fixed upstream so probably it'll trickle to ubuntu soon... (?)

---

### Post by CloudFX on 2008-08-01
Heh, that's a weird bug :).  And yes, it's been marked as Fix Released so it will probably be gone in Alpha 4.

---

### Post by ronacc on 2008-08-01
It looks to me that the "fix" upstream only addresses the "double mount" part not the cannot mount as "user" part , I will open a seperate bug on that .

edit: opened bug#254098

---

### Post by Gina on 2008-08-02
Good. Thank you.

---

### Post by wlake on 2008-08-04
I don't know if this has been reported elsewhere, didn't find in a search. As far as the double storage media (partition) icons are concerned. For me with Ubuntu II 64 bit, I found if I Ctrl-Alt-Backspace once or maybe twice logging back in each time the doubling part goes away and only the single icons are there. I wonder if anyone else has noticed this behavior?

Regards,
wlake

---

### Post by waspbr on 2008-08-04
dunno if it is relevant, but the double-mount issue (in my case at least) only comes up when  you mount something after booting/logging in, if you mount something through fstab, then the double-mount problem doesn't come up, just fyi.

---

### Post by ronacc on 2008-08-04
yes the "double mount " only occurs for devices not mounted through fstab .

---

### Post by scradock on 2008-08-04
> **ronacc said:**
> yes the "double mount " only occurs for devices not mounted through fstab .
but I have noticed several times that loading from fstab fails during boot, so that I end up with NO icon for another partition, and have to remount. Even if I do that by "sudo mount -a" in the terminal (which uses fstab) I get the double icons.....

---

### Post by ronacc on 2008-08-04
the original bug says fix commited so it ahould show up soon , if it doesn't fix it file a new bug .

---

### Post by autocrosser on 2008-08-04
Well-The nautilus update from this evening did not change much--I am looking towards the next few days...I would say that we "should" see it by weeks end (cross-fingers):)

---

### Post by matthewbpt on 2008-08-04
i get the double icons too, but also whenever i mount any media, be it a cd, dvd, pendrive or ipod, the following error comes up

```
Could not mount. DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered 
```

But they mount anyway and still work (though showing double) and give a lot of trouble dismounting. Any thoughts on this?

---

### Post by autocrosser on 2008-08-04
Yes--that is one of several errors currently--take a look at the Launchpad bug (posted on pg1) & see if you can add anything to it---the Devs are talking about this as much as we are........

---

### Post by autocrosser on 2008-08-05
The GVFS updates as of this evening 8/5/08 have "cured" the problems with double mounting---at least with my system--FYI--I use the main mirror & if you are using a country mirror your update might be later......

---

### Post by ronacc on 2008-08-06
Yes the updates cured that one but now I have 2 fun new ones, up arrow in a term window dosent scroll it takes a screenshot and then rightclick on the screenshot and selecting delete to cleanup my desktop crashes gvfsd ??
added comments to already reported bug#251910 .

---

### Post by Gina on 2008-08-06
I downloaded the latest daily build Live CD to try on my P3 but that's giving trouble so tried it on P4 - the double icon bug is fixed :)

Actually, I don't think the Intrepid Live CD is the problem with my P3 desktop - I think it's on it's way out.  I'm getting various errors on things that were working.

---

### Post by ronacc on 2008-08-06
Gina backup that one quick , the HD may be going out .

---

### Post by Gina on 2008-08-06
Nothing important on it anyway - just a successful Hardy install, an unsuccessful Intrepid install and a virtually unused /home partition.  I only use it for testing.  It's only a 10GB hard drive :lolflag:

I may try swapping bits around with another old box I've got.

---

