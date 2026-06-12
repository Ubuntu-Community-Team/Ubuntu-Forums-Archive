---
title: "How to install Kernel 2.6.33 with GRUB"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by criticalsmile on 2010-03-07
Ok, I really like 9.10 Ubuntu. The trouble is, I can't seem to download the Kernel source, compile and install. I struggled just to get it comfigured and compiled. Now...past all of that, how can I get the Kernel installed and Grub.conf ready?

My new compressed and ready to go Kernel is in the /boot directory just waiting for me to test it and for it to fail (hehehe. Ok, it might work the first time. Bwah hahaha!). Trouble is, where does GRUB find it? How can I point Grub to the files? I use to manually edit grub.conf but now it's setup from some mystery script.

I likes me some changes but a little stumped here and kinda tired of fighting this for days. Online searches turned up nothing.

NOTE: While searching for the solution I found this.

**make ARCH=x86_64 defconfig**    <-- To set up correct arch?    
**make -J4**     <--  for dual processor. J8 for quad
**make gconfig**   <-- Stuggled to fill the dependencys for this but makes config so easy.
                          Then go back to make menuconfig to get what gconfig didn't get.
**make allnoconfig**  <-- clean it out.

Love to hear more on how to optimize/tweak my 2.6.33 for dual AMD CPU and ATI HD3200. I need World Of Warcraft to run smoother in WINE. (sound dies after 5 mins. *sigh*)

Thanks in advance for help with Kernel install.

---

### Post by criticalsmile on 2010-03-08
UPDATE: I passed some GRUB command, which was really stupid, and it somehow modified the grub.conf file adding my new kernel. The Kernel was not working of course. I'm sure I left important modules out (first time is always epic failure).

Does anybody know what GRUB commands to issue to get the new kernel added to the boot menu? The grub.conf says NOT to edit manually. :-(

---

### Post by 9tails on 2010-03-09
Follow the steps in this guide: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

you'll get two .deb files that you can install using dpkg as documented in the guide above

Edit: alternatively you can also use "kernelcheck" to install the new kernel automatically, or follow this guide to install a precompiled 2.6.33 kernel for ubuntu: [http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/)

---

