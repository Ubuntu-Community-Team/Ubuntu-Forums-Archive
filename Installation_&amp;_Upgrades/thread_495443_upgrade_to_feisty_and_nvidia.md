---
title: "upgrade to feisty and nvidia"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by bala.variyam on 2007-07-08
Hi,

I am running Edgy and want to upgrade to Feisty.  I have installed the nvidia drivers from [http://www.albertomilone.com/instructions.html](http://www.albertomilone.com/instructions.html) so that i can get 1600x1200 resolutions on my display.

Can someone tell me, if I upgrade to Feisty, will the driver continue to work?  if it wont, what do I need to do to get higher resolutions on my monitor?

thanks,
bala

---

### Post by confused57 on 2007-07-08
> **bala.variyam said:**
> Hi,

I am running Edgy and want to upgrade to Feisty.  I have installed the nvidia drivers from [http://www.albertomilone.com/instructions.html](http://www.albertomilone.com/instructions.html) so that i can get 1600x1200 resolutions on my display.

Can someone tell me, if I upgrade to Feisty, will the driver continue to work?  if it wont, what do I need to do to get higher resolutions on my monitor?

thanks,
bala
No, your current Nvidia drivers won't work with a different kernel...you'd probably need to set your video driver to "nv" or "vesa" and uninstall your current Nvidia drivers(the site you used to install has instructions for this), before you upgrade to Feisty...then you can install Nvidia drivers for Feisty:
[http://ubuntuforums.org/showthread.php?t=432056&highlight=Nvidia+Feisty](http://ubuntuforums.org/showthread.php?t=432056&highlight=Nvidia+Feisty)

I would recommend you back up any important data, dist-upgrades have been known to fail.

---

