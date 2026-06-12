---
title: "Error when adding applications"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by jide on 2008-01-21
Hello Ubuntu friends,
I have problem each time I tried to add an application through synaptic package manager. I always get an error:

*E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1*

The error started when I wanted to install bcm43xx-fwcutter and the download access address was no longer in use (broken). Although I later installed the bcmCutter using another address, since then I continue to get the above error message. I removed the internet address (for bcmCutter) from the third-party software repository but still continue to get the error message each time I add an application.

Please can someone help me to solve the problem.

Thanks a lot.

---

### Post by Whiteice on 2008-01-21
Ok try goin into system/administration/software sources and selecting all the check box under the tab ubuntu software. Then try to get the package again.

---

### Post by jide on 2008-01-23
Hello,

I just did as you said but the problem still persist. Do not know the next step to take.
 
Thanks,
Jide

---

### Post by rosegarden78 on 2008-01-23
I use this package personally for my own card.  Try this at a terminal

sudo modprobe bcm43xx

Google for a third-party source to download the bcm43xx debian package if the command above fails then install new bcm43xx package and repeat step above.

---

### Post by jide on 2008-01-30
Thanks friends,
I solved the problem by removing bcm43xx (all the configurations) totally from the synaptic package manager.

Jide

---

