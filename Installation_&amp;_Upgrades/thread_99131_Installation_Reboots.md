---
title: "Installation Reboots"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by Remdul on 2005-12-05
Howdy,

I am currently trying to install Ubuntu onto a compaq machine (no floppy drive) with an official Ubuntu installation CD. This is quite interesting, since at the installation screen, where it says "For the defult installation, press ENTER", when I hit enter, it reboots my computer, and loads back to this very screen, allowing me to get nowhere. At first, I thought it was a memory error, so I ran memtest86, to no avail. Does anyone know the cause and perhaps how to fix this? Thank you,

Remdul Me'Rim
 (Bryan)

---

### Post by blueplazma on 2005-12-05
You might try loading the kernel with the minimum of options needed to boot.  A good strategy is to load the kernel with many options disabled, then add them back in until you figure out the issue.

---

### Post by Remdul on 2005-12-05
I have already tried this also. It still reboots, strangely enough.

---

### Post by The Moth on 2006-01-03
I am having the exact same problem with, coincidentally, a compaq. I installed on my HP laptop and everything went fine. This Compaq is throwing a hitch in my giddy-up. Any help will be greatly valued! - Moth

---

### Post by Zhanna on 2006-01-03
I'm very new to Linux so there may be a better solution, but what solved this very problem for me (when installing on my HP desktop system) was to use the command **linux acpi=off** rather than just pressing Enter for the default installation.  Everything went without a hitch once I tried that.

Zhanna

---

### Post by The Moth on 2006-01-04
Shiny! She'll fly now. Thanks Zhanna. That worked perfectly! - The Moth

---

### Post by Zhanna on 2006-01-04
Excellent!  :D  You're welcome.  Have fun!!!

Zhanna

---

