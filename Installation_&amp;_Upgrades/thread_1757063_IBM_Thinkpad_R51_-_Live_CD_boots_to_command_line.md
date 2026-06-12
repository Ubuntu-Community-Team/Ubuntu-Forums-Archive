---
title: "IBM Thinkpad R51 - Live CD boots to command line"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by bkb on 2011-05-13
I am trying to install lubuntu 11.04 on an ancient IBM Thinkpad R51.  I wanted to try the Live CD to make sure there would be no issues.  However, it boots to the command line not into LXDE.  I checked the CD for defects, there are none.  I tried Alt+F7 but its just a black screen.  Could someone please help me troubleshoot & fix.  Much appreciated - thanks.

---

### Post by bkb on 2011-05-13
I also tried this but it didn't work:

[http://ubuntuforums.org/showthread.php?t=1513792](http://ubuntuforums.org/showthread.php?t=1513792)

---

### Post by bkb on 2011-05-13
These reconfigure commands followed by startx didn't work either:

[http://ubuntuforums.org/showpost.php?p=1805121&postcount=6](http://ubuntuforums.org/showpost.php?p=1805121&postcount=6)

---

### Post by bkb on 2011-05-13
Sadly adding this boot option to the LiveCD didn't do anything for me either:

```
i915.modeset=0 xforcevesa
```

---

### Post by Hedgehog1 on 2011-05-13
How much RAM is on this system?  Ubuntu needs at least 512 meg to run.  Lbuntu will run in 256 meg.

***The Hedge***

:KS

---

### Post by bkb on 2011-05-13
256 that's why I went with lubuntu

---

### Post by bkb on 2011-05-13
This suggestion worked:

[http://ubuntuforums.org/showpost.php?p=9620233&postcount=9](http://ubuntuforums.org/showpost.php?p=9620233&postcount=9)

I managed to get into LXDE and everything works fine.  I guess I'll just take a leap of faith and go for it and deal with whatever issues come up post install...

---

### Post by Hedgehog1 on 2011-05-13
Sorry - it was right there in your first post.  Missed that.

---

### Post by bkb on 2011-05-13
Any idea what this might be, given the workaround?

---

