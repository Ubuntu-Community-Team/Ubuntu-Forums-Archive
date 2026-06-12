---
title: "ATI driver broken with upgrade to Feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by DrQuincy on 2007-04-23
I had Edgy Kubuntu and did the upgrade through the package manager today. I had flgrx working on my ATI card but now it's broken (it outputs Direct Rendering: No). It runs really slow and if I use my old xorg.conf file - one that worked under Edgy - it won't boot and I have to do dpkg-reconfigure xserver-xorg from the shell.

Any ideas how to fix it?  Do I have to install a different version of the ATI driver or something?

Thanks.

---

### Post by bulldog on 2007-04-23
If you're upgrading to Feisty you have a new kernel.
You need to reinstall the restricted modules and you graphics driver.

---

### Post by DrQuincy on 2007-04-23
Thanks.  Sorry, I'm pretty new to this - can you point me to something to help me do that?

---

### Post by KeeNeR on 2007-04-23
> **DrQuincy said:**
> Thanks.  Sorry, I'm pretty new to this - can you point me to something to help me do that?

Here's some [reading]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") to how to install the ATI driver.

---

### Post by wyth on 2007-04-23
Depending on the ATI card you have, it may work, it may not.  I fought with it for about a month, since beta.  I couldn't get fglrx to work with my old card in xorg 7.2, and ended up rolling back to Edgy.

---

