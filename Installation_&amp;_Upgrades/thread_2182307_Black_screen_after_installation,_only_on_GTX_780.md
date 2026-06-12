---
title: "Black screen after installation, only on GTX 780"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by wujj123456 on 2013-10-20
I just tried to install 13.10 release.  Last time I wasn't able to get 13.04 to work on my machine.  I am using 4770K + GTX780 in SLI.  So far, this is my experience:

1) With GTX cards in SLI, liveCD won't boot
2) Leave only one GTX780 card, I was able to boot LiveCD and perform the installation.  After the installation and various bootloader fix, I can select Ubuntu for booting, but I had a black screen.  Even recovery mode is not coming up.
3) If I uninstall all GTX cards, I was able to boot the exactly same installation.  Then I manually removed nvidia-current and installed nvidia-319 (which has 780 support).  After the installation, the system still boots fine as long as I have Nvidia cards unplugged.  If I plugin NV cards, it's again a black screen, and even recovery mode is not coming up.

I can see that it hangs the moment it loads nv module.  Any ideas?

[IMG]https://dl.dropboxusercontent.com/u/17011409/Ubuntu13.10RecoveryBoot.jpg[/IMG]

---

