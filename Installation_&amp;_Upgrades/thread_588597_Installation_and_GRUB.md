---
title: "Installation and GRUB"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by thetimekeeper on 2007-10-23
I have a previous install on an ext3 partition, that dual booted fine with my XP, using Ubuntu 7.04.

After formatting the ext3 partition to do a fresh install of 7.10 from the livecd, I chose / as a mount point, and decided not to install grub because I thought it would conflict with my Windows bootloader.

Woe, joy, behold, I click Ubuntu Linux from my Windows Bootloader, and it brings me to a GRUB command line, where /boot/grub/stage1 or anything cannot be found using the find command.

Besides my knowledge of those commands, I am basically a linux newbie. I feel kind of let down, having read a lot of good reviews about the ease of Ubuntu 7.10's install and usage...


Any help and advice would be appreciated!

---

### Post by Robor on 2007-10-23
I haven't done a dual boot setup in a while but I think most people usually install Windows first then install Ubuntu and install GRUB.  Last time I did that it detected my Windows install and had it as a bootable option under Other OS's at the bottom.  Maybe try that?  Even if it did screw up your Windows boot you could fix it with a /fixboot /fixmbr from the XP recovery console.

---

### Post by thetimekeeper on 2007-10-23
Hi,

Yeah, XP was installed before. When I had 7.04, I could just select Ubuntu from the Windows boot loader and boot into Ubuntu fine.

---

