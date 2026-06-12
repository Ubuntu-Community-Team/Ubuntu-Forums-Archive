---
title: "Dapper custom install?"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by Mr_E on 2006-07-10
Is there any way to do a custom install (I don't want the office suite, gimp, etc.).  I couldn't find an option to.

Apparently you used to be able to enter "server" at a prompt on prior versions (from what I can tell from other postings) for a minimal install, and you could add from there.

I COULD go plain Debian, but Ubuntu is the first distro I've found that handled most of my hardware so easily...

Did the latest build hide or remove this ability?
I'm guessing the server install CD wouldn't auto install the kernel and support modules I want for a laptop.

I checked ouu Xubuntu, but it still has extras I don't need..

TIA
-KWE

---

### Post by 5-HT on 2006-07-10
You can still do a barebones server install using the alternate CD (not the server CD). Easiest way is to press 'Esc' at the menu for a boot prompt and enter 'server'.

After the install, you will have a console-only (no X) minimal system that you can add to.

The server install will still autodetect hardware and try to load the correct modules. In addition, you'll still receive the same kernel as you would doing the install from the desktop/live CD (though you may want to change it for SMP support or other if applicable).

Hope that helps.

---

