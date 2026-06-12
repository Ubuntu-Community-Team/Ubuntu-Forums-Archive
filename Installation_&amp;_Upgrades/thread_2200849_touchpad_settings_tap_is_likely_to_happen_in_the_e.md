---
title: "touchpad settings: tap is likely to happen in the end of scrolling"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by k-neko on 2014-01-21
Hello forums! 
My name is Mike & I'm coming back to linux after a couple of years with Mac OS. 
atm I'm using OpenSuse, but back in the day I've used debian deriatives and rpm, yast, zypper and such frustrate me a lot.
However, OpenSuse has nice default settings for my touchpad which I can't even google how to set up on ubuntu (which to be honest was the only reason to install it: I didn't want to do much documentation reading/ setting up with Linux, wanted it to be out of box.)
Well..
 On kubuntu live, touchpad is rather strange. When I scroll web page with 2 fingers for less than a second, it is treated as page scroll PLUS two finger tap. If I scroll for at least a second, problem is not in there. 
How do I set this up?


Edit: just realized that "Installation and upgrades" is not the valid forum for this.. sorry :<

---

### Post by k-neko on 2014-01-21
okie-dokie, now its' fixed!
if you encounter such weird stuff & will dislike it, just do:
$ synclient MaxTapMove=100

(e.g. lower MaxTapMove to some reasonable value)
;)


Related params are also 
```

    MaxTapTime              = 180
    MaxTapMove              = 100
    MaxDoubleTapTime        = 100

```

---

