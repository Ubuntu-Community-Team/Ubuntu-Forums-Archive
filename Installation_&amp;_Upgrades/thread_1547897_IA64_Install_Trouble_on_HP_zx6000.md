---
title: "IA64 Install Trouble on HP zx6000"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by webghost on 2010-08-07
Hi,

I'm trying to install the IA64 version of Ubuntu 10.04 LTS server on an HP zx6000. I'm using a boot CD to do this. It boots just fine to the installer but after setting up my language options, it complains that it can't detect a common cd-rom drive. When I choose to manually load modules, it gives me a menu that says Modules Required for CD-Rom drive: none. So I'm forced to abort the installation. Both the hard drive and the cd-rom drive on this computer look to be SCSI.

In a desperate attempt to gain a little ground, I did manage to get Ubuntu 6.06 server (IA64) to install without a hitch. So... it would seem that it's certainly should be possible to get a current version of Ubuntu to install. 

Does anyone have any suggestions for what to try next? With 6.06 installed, is there an upgrade path I can take to get to 10.04 LTS? If so, can you help me out with how to do that? Or, is there some magic voodoo I can do to get the 10.04 LTS server installation to work? I read this thread [http://ubuntuforums.org/showthread.php?t=973831](http://ubuntuforums.org/showthread.php?t=973831) which suggests switching to a second console and using the command "modprobe ide-scsi" but this solution did not work for me.

Thanks in advance for the help.

---

### Post by dino99 on 2010-08-07
kernel 2.6 issue:

[http://www.linux.com/archive/feed/33164](http://www.linux.com/archive/feed/33164)

Linux kernel has eliminated the ide-scsi module.

---

### Post by webghost on 2010-08-07
Thanks dino99, a very interesting read. Linus certainly is opinionated, but who can really blame him? I believe Ubuntu 6.06 is using version 2.6.15 of the kernel and it does indeed work... Certainly this article explains why the command listed in the other thread does not work, but I'm still at a loss for how to solve the larger problem of being unable to install 10.04.

---

