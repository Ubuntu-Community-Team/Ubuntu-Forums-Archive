---
title: "Virtual PC 2007 and Ubuntu 7.10"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by deeksy on 2008-03-25
Hi,

I'm trying to install Ubuntu 7.10 Client onto a Microsoft Virtual PC 2007 virtual machine and am coming up with the following issues after choosing 'Start Ubuntu in safe graphics mode' or 'Start or Install Ubuntu' from the first menu:
 After a little while, I get the following messages:
   * [ 68.749096] isapnp: checksum for device 1 is not valid (0x89)
   * [ 68.758637] isapnp: checksum for device 2 is not valid (0.xbe)
 * and then after the Ubuntu splash screen (which appears fine), I get dumped to the Busy-box built in shell with the following error message:
   * /bin/sh: can't access tty; job control turned off

Does anyone have any suggestions?  I have configured the virtual machine to use operating system: other and assigned it 256MB of RAM.  Any other ideas?

---

### Post by luisromangz on 2008-03-25
If you can, don't use VirtualPC to virtualize Linux. Try VirtualBox or the free VMWare version.

---

### Post by erginemr on 2008-03-25
Please try this:
[http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control)

I can also suggest you to use VirtualBox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) instead if you are not bound to using Virtual PC and I suspect, M$ people are trying again to make Linux users' life hard.

---

