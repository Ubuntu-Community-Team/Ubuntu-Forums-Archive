---
title: "Resuming Edgy Installation"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by Jamie Jackson on 2006-11-14
I've been through weeks of installation problems, but I finally got the installation going with a network install.

Anyway, I got through the first part of the installation. Then, I chose the finish installation option (which reboots and finishes the installation). The machine rebooted and I selected Ubuntu from the GRUB menu. However, I got:

BUG: soft lockup detected on CPU#0!

...and the startup hung.

Then, I rebooted, and chose Ubuntu from GRUB again, but I'm dropped to the command line. I can login and everything, but I need the installation to pick up where it left off. How do I give it the kick to resume?

Thanks,
Jamie

---

### Post by Jamie Jackson on 2006-11-15
FWIW, I'm looking at the install instructions [here]("https://help.ubuntu.com/community/Installation/I386"), and I notice that it asks for timezone and login information in "Stage 2" (after the reboot). I thought I remembered that being in stage 1, but in any case, I did get through those steps. My error came somewhere after these dialogs.

---

