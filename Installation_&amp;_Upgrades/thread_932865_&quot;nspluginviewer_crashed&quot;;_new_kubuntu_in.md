---
title: "&quot;nspluginviewer crashed&quot;; new kubuntu install on knoppix system"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by pterandon on 2008-09-28
Hello.

I have an Aptiva  computer that had a Knoppix installation on it.  I tried a dist-upgrade in Knoppix and it did not go well. :(  So, I installed Hardy Heron on the box, saving the /home as-is, but formatting everything else.

Now, with the new kubuntu 8.04 install, I get this message upon boot-up:

KDE Crash Handler
"The application unknown (nspluginviewer) crashed and caused the signal 11 (SIGSEGV)."

Do you think this is  a legacy of my Knoppix install, a bug in Heron, or something I could easily fix myself? 

thanks!

---

### Post by cariboo on 2008-09-28
It may well be, I would suggest you backup your bookmarks and then delete ~/.mozilla, this is the directory where Firefox stores all it data and settings.

Jim

---

