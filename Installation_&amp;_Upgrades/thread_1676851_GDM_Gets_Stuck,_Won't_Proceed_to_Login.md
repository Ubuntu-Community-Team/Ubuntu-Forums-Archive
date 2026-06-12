---
title: "GDM Gets Stuck, Won't Proceed to Login"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by ScottCh on 2011-01-27
Hi Folks,

When I boot my laptop to Ubuntu Lucid, it boots to a blank purple background screen.  It doesn't matter how long I wait.  I can move the mouse cursor but there's nothing to click. I can ctrl-alt-F1 and log in to a text prompt.  When I list the processes I see that gdm is running.

All I did to create this mess was attempt to install the KDE marble application.  It requires the KDE and Qt infrastructure, many packages. I've gone through the process before and it worked.  However, with my laptop the next time I rebooted Ubuntu, GDM wasn't working.  The machine is reasonably powerful and has 2 GB of memory, so it's unlikely to be a resource issue.

I've scanned /var/log/Xorg.0.log, and don't see anything significant there.  There's a brightness file missing that ACPI wants.  That's it.

I've tried reinstalling GDM and ubuntu-desktop using apt-get.  No help there.  The problem was unchanged.

Anyone have an idea what I should try next?

Thanks muchly!

Scott C.

---

