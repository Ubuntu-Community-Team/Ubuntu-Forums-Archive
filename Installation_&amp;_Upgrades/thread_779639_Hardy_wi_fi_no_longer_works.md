---
title: "Hardy wi fi no longer works"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by paul_r_jacobs on 2008-05-02
After upgrading to hardy my wifi no longer works.  System>Admin>networks no longer shows wifi at all.

Any help appreciated...

---

### Post by Webdemic on 2008-05-06
What sort of hardware are you running? Anytime you update the kernel, you run the risk of "losing" hardware.

If you are unsure as to what wireless card you have, an easy way to check is to open a terminal, and type:

lspci

This should show you all of your peripherals. Look for something that says "wireless". That should also indicate the chipset that the wireless card uses.

Please post the output of the above command. Thanks.

---

