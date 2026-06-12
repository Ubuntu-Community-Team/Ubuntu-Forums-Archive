---
title: "Upgraded now no video!"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by biggrimtim on 2006-09-03
Hello I upgraded from Breezy to Daper with online update and now I have no display.  It gets to the login because I can hear the login sounds.  Please help!

Thanks in advance.:confused:

---

### Post by goatflyer on 2006-09-03
You're not alone, here's the fix for it.

[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)

---

### Post by biggrimtim on 2006-09-04
Thanks but thats not my problem. I have a black screen.  I did try the steps listed and it said I have the newest version.  Any other suggestions.

---

### Post by taurus on 2006-09-04
Need to get to another console, <Ctrl><Alt>F2, and reconfigure your X again...

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by biggrimtim on 2006-09-04
Thanks, I tried that also and it still does'nt work.  Any other options?

---

### Post by BrokenBrick on 2006-09-04
I have the same problem with a fresh install of dapper drake.  I make it to configuring packages, and when it gets to xorg the screen goes black and the machine hangs altogether.  Since I have nothing installed I can't switch to a console to correct the problem.  So I am guessing that this means that this problem is included on the latest dd iso build.  Or else my computer is just stupid :(

---

### Post by biggrimtim on 2006-09-07
Not sure I wish we could figure this out.  I went back to Breezy for now.  I am Lost.

---

