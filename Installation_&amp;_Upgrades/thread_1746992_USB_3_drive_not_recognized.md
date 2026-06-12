---
title: "USB 3 drive not recognized"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jhoremans on 2011-05-02
External USB 3 drive not recognized after upgrade to Natty.
Works fine and is recognized immediately when plugged into USB 2.
Occasionally the drive is recognized with USB 3 when plugged/unplugged.

Worked fine in Maverick (with USB 3)

---

### Post by sokola on 2011-05-17
Same problem for me on asus u36jc. Worked fine with Ubuntu 10.10; then with Natty it started first to freeze, and after a kernel update, it simply began not even recognizing the drive. Power gets through, though, I can see my external's led flashing...

---

### Post by Hulles on 2011-06-02
See these posts:

[http://ubuntuforums.org/showthread.php?p=10832032](http://ubuntuforums.org/showthread.php?p=10832032)
[http://ubuntuforums.org/showpost.php?p=10831338&postcount=15](http://ubuntuforums.org/showpost.php?p=10831338&postcount=15)

This worked great. My USB 3.0 port on my ASUS G73SW now functions and handles my external drive. Btw, the second post is the more succinct answer if you know what you're doing. Also btw, I used the "pci=msi" without the "aer" param.

I hope this helps.

---

