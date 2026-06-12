---
title: "automatic upgrade faied in vmware player"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by JohnnyWalker on 2006-07-03
I tried to do the automatic distribution upgrade in wmware, and when it was finished and rebooted,X fails to start, with a blue screen saying that x is likely not set up properly.

How could this happen, is it a vmware player specific problem? 

What can I do to get it working again?

---

### Post by matthew on 2006-07-03
I'm basing this on the assumption that you mean X has failed within the vmware player, not your xserver as a whole.

In the vmware installation, at a command prompt, type "dpkg-reconfigure xserver-xorg" and follow the prompts. You should be able to just hit "enter" for each. The only one to take a look at is make sure the vmware video module is being used.

---

