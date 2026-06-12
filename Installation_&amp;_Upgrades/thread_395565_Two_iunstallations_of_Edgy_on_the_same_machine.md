---
title: "Two iunstallations of Edgy on the same machine"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by apastuszak on 2007-03-28
I have a PC with two SATA drives in it.  The primary SATA drive has Suse 10.2 on it, which I don't use, and the secondary drive has Edgy 6.10 on it, which is my primary OS.  I would like to reformat the 40 GB HD and install Edgy+LinuxMCE on it.

After I do this, I want to be sure I can boot into the secondary HD and continue to use my current Edgy install.

Is it as easy as adding something to my grub.conf file after the install, or will the installer pick up the Edgy install on my second HD and add it automatically to my boot menu?

Andy

---

### Post by tonym on 2007-03-28
I tend to add to the Grub config.  In the example there is the config for accessing a Windows system.  I use the same syntax pointing to the /boot partition of the secondary system.

Regards

Tony.

---

