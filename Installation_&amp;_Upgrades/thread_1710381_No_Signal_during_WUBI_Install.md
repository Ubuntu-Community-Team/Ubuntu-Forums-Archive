---
title: "No Signal during WUBI Install"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by moonscapex on 2011-03-19
After restarting my computer from the WUBI installer, I select Ubuntu, wait a minute, then get a blank screen. The same happens on the live CD. My monitor (an HDTV hooked up with the VGA port) displays No Signal. What should I do?
Thanks.

---

### Post by bcbc on 2011-03-19
What graphics card do you have?

---

### Post by moonscapex on 2011-03-19
I forget - but it's a restricted driver. (I an older version of Ubuntu a while ago on a different monitor).

---

### Post by bcbc on 2011-03-19
have a look in windows: device manager, display adapters.

If it's nvidia use nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (special instructions for Wubi in post #8)

---

### Post by moonscapex on 2011-03-19
Thank you very much, it worked. Hopefully this'll be fixed in the next version of Ubuntu.

---

