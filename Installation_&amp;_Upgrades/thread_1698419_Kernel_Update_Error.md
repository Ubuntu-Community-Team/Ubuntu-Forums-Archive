---
title: "Kernel Update Error"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by squid636 on 2011-03-02
I was prompted today to install upgrades from the Ubuntu Software Center.  After installation I rebooted and when trying to use the new kernel my computer encountered an error. Any suggestions?  Thanks.

---

### Post by regala on 2011-03-02
> **squid636 said:**
> I was prompted today to install upgrades from the Ubuntu Software Center.  After installation I rebooted and when trying to use the new kernel my computer encountered an error. Any suggestions?  Thanks.

well, it means exactly that either the initramfs created during the post triggers (mkbuildinitramfs) of new kernel package installation, doesn't ship the correct kernel module for the filesystem you use as root fs, either the kernel module wasn't shipped at all in the kernel package, or the initramfs scripts are buggy.
either way, it's a shame from a distro that so claims it's soooooo coooooooooool.... you should open a bug report on linux-image at least.
you can try rerunning by hand mkbuildinitramfs (look at the man page first) to see if it would create a correct initramfs. Either way, this kind of mistake on "stable" releases is very disappointing. Ubuntu clearly loves to break people's stuff.

---

### Post by squid636 on 2011-03-07
I fixed the problem by going in Synaptic Package Manager and reinstalling the packages for that kernel version.  There were three of them.  Upon rebooting everything is working correctly.

---

