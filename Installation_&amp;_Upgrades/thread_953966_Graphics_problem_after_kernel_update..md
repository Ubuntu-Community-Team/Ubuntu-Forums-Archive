---
title: "Graphics problem after kernel update."
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Timtro on 2008-10-20
Hi All,

This is related to a previous post:
   [http://ubuntuforums.org/showthread.php?p=5984248#post5984248](http://ubuntuforums.org/showthread.php?p=5984248#post5984248)

So after the update to 2.5.24-21 failed, I deselected it, as well as some older kernels from synaptic, applied, applied other updates and then rechecked the 2.5.24-21 kernel image and modules.

Now, when I select the 2.5.24-21 kernel from Grub, I don't get an fsplash, and when X starts, I get a box saying that I'm in low-graphics mode and I need to configure if I want to have my bells and whistles. I didn't want to go writing over all of my config files. I have a duel head setup that I don't want to bugger up, so I just restarted and selected the 2.5.24-19 kernel, and things went like normal.

How do I fix the 2.5.24-21 kernel? Is it worth the trouble?

Thanks a million.

Best regards,


Tim.

---

### Post by Timtro on 2008-10-31
*bump*

---

### Post by cubbybear on 2008-10-31
If your machine has trouble with a newer kernel, which sometimes happens, you can keep using the 2.6.24-19 kernel which performs well on that computer.  You can also wait and try updating to the next newer kernel when it comes out, which often fixes previous kernel problems.  With the new 8.10 release it updates to 2.6.27-7 kernel which is working much better for some.

---

