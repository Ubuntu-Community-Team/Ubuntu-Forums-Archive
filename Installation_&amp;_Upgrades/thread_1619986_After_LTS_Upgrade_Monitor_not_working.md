---
title: "After LTS Upgrade Monitor not working"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by rambo15 on 2010-11-12
Good Afternoon:

I have a Dell 8100 with an NVIDIA graphics card. I had previously installed Ubuntu Hardy Herron and everything worked fine.
Today I upgrade to LTS. The system rebooted and the Grub boot loader displayed my list of O/S when I selected the LTS, the monitor shutdowns and displays a message about best resolution should be 1280 X 1024. 

Anyone have any suggestions on how to fix this?

Thanks

---

### Post by sikander3786 on 2010-11-12
Hi.

From the Grub menu, highlight the first entry and press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot and see if it gets to the desktop this time. You'll later need to activate proper drivers from System > Administration > Additional Drivers to say good bye to that problem.

Please let us know about your progress.

---

