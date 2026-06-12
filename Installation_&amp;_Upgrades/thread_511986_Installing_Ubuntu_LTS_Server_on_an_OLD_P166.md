---
title: "Installing Ubuntu LTS Server on an OLD P166"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by mike_d on 2007-07-28
I'm having trouble getting Ubuntu LTS Server to run on an OLD Pentium-166 I have lying around.  I know the hardware is good, as it was running Gentoo last week.  I install LTS from the CD with no issues, the installation completes like the 100's of other times I've installed Ubuntu on other machines.  The problem is that when the installation completes and it reboots, it goes through the power on self test, then loads grub.  I get the standard output that you get when you first load the kernel, after the lines "savedefault" and "boot" appear on the screen, the computer just reboots and goest to the power on self test again.  It will cycle endlessly like this and never actually boot.  

Any ideas?  

The computer is a P166, 256M of ram, and 2-2G HDDs
No errors show up anywhere
The installation is the default LTS server from the CD

Thanks,
Mike

---

### Post by louieb on 2007-07-28
Is the processor is a P1 **(586 class processor)?** I tried to install Ubuntu server on a P1 200. It was a no go found that the server CD kernel requires a **686 class processor** that is a P2 or better. To get a server installed on a P1 you can use the Ubuntu alternate CD and do a minimal or server install from it.

---

### Post by mike_d on 2007-07-28
Ah ha!  I bet you're right.  I'll get the alternate cd and give it a try.

Mike

---

