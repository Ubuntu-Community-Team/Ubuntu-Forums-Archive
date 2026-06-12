---
title: "Cannot install or boot 10.10 (dual boot with windows 7)"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by defmer on 2010-10-19
I am trying to install Ubuntu on a machine that already has Windows 7 on one partition. Obviously I intend to install it on the other free partition.

So I downloaded the iso burnt it onto the disk and pop in the disk and the boot the machine. The installation screen comes up I selected the first option (Try Ubuntu without installation), I just see a prompt after a few seconds and then the screen goes blank and nothing happens. Unable to detect a signal, The monitor goes into standby. The same thing happens if I use "install Ubuntu" option as well. 

so I downloaded minimal install version Ubuntu and tried to install with that. since its old school installation, the installation completed without any errors, but when I restart the grub come up and when I select to boot into Ubuntu, I see the same behavior i.e. the screen goes blank and never boots to anything. 

This is a machine on which I was using 10.4 until yesterday.

so please let me know you view and suggestions. This issue is really eating me out. :confused: 

thank you

---

### Post by sikander3786 on 2010-10-19
Pointing to the first entry on Grub menu, press 'e' to edit it. Using arrow keys, navigate to 'quiet & splash' delete them and type 'nomodeset' in their place. Press Ctrl + X to continue booting. Can you see the desktop now?

Which graphics card are you using? You will need to install the proprietary drivers in order to correct that problem permanently.

---

