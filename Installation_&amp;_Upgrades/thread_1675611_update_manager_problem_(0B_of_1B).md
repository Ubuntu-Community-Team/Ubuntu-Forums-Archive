---
title: "update manager problem (0B of 1B)"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by graham45 on 2011-01-25
I was  notified this morning (26 Jan) that updates were available for my ubuntu 10.10 (on dell 64bit system)  The only odd thing was a message came up saying a partial update only was possible, which then seemed to work ok. I thought if it was a partial u/g then what packages may still need upgrading ? On running update manager and manually checking for updates i get "downloaded 0B of 1B" !!    I have tried a number of apt-get commands to clean up the issue but it persists still.  Does anybody have any ideas I can try to rectify this.   I have looked at the source list and it seems OK !

---

### Post by mörgæs on 2011-01-26
Which apt-get commands have you tried?

---

### Post by Rubi1200 on 2011-01-26
What does ```
sudo dpkg --configure -a
``` show? Are there errors?

---

### Post by The_Blue_Bomber on 2011-03-05
Same problem....

Any solution ?

---

### Post by Hedgehog1 on 2011-03-06
> **graham45 said:**
> On running update manager and manually checking for updates i get "downloaded 0B of 1B"...
I have looked at the source list and it seems OK !

graham45, (and The_Blue_Bomber),

This is completely normal behavior when there are currently no additional updates for your version of Ubuntu.

You are up to date.

***The Hedge***

:KS

---

### Post by The_Blue_Bomber on 2011-03-06
Hope your right...never really noticed it before...

But thanks,

The_Blue_Bomber

---

