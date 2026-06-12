---
title: "Upgrading Ubuntu broke my ssh keys...how do I use the same keys again?"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by machinus on 2015-12-19
I was using Kubuntu 14.04. I upgraded to the latest version, and now my ssh aliases are broken. My .ssh folder is there, but they keys don't seem to be working anymore.

Is there a way to reconstitute my login information so that I can use it again? Meaning, how do I reconfigure my ssh to find the keys without having to recreate them?

***I did not realize dsa keys were no longer accepted by default. My server still uses them.***

---

### Post by QIII on 2015-12-20
Hello!

If you happen to come back around to this, would you be so kind as to share the solution so that others may benefit.  While we are glad that you found your individual solution, this is a community support forum where we hope all can learn from each other's solutions.

Thanks.

---

### Post by lliseil on 2015-12-20
Well it seems OP used a DSA key and that what caused the trouble:

>  ***I did not realize dsa keys were no longer accepted by default. My server still uses them.*** 
Things evolve; ssh is one of them :)

---

### Post by QIII on 2015-12-21
Thank you for the observation.  I quite well understood that.

Others, however, may not.

---

