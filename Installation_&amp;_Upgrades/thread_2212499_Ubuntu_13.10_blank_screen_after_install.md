---
title: "Ubuntu 13.10 blank screen after install"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by Adrian_Verster on 2014-03-21
I'm installing Ubuntu 13.10 on my Acer aspire V5-472 in UEFI mode, and I've completely wiped the windows partition off. Everything installs fine, except that the screen stays blank after install - I can tell its at least partly on because if I increase the brightness the screen brightens but stays blank. Furthermore the computer is booting because if I plug in a monitor, it works and I can log in and use the computer.

One thing I've tried doing is booting with 'nomodeset' option. This briefly shows the ubuntu logo while booting, but then kicks me into a command line version. I can log in and if I try to use 'startx' but it tells me there are no screens or displays available. However, if I instead install Ubuntu in Legacy mode instead of UEFI, I get basically the same problems, except that 'nomodeset' allows me to load Ubuntu. Here the external monitor won't work and I cannot adjust screen brightness - I assume this is because nomodeset disables a lot of graphics drivers?

Any help to understanding why I'm getting a blank display on my laptop screen, but not the external monitor would be a huge help!

Adrian

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
Don't know, but until somebody has a more specific suggestion, I'd open synaptic using your external monitor and experiment with different graphics drivers. I haven't used the default 13.10 but there used to be a menu item where you had to explicitly "opt in" to use propietary drivers. If there still is, that might help. You may wind up with some sort of gui program to adjust settings for the driver. For me, for instance, it is "nvidia-settings". If you have something like that, I'd look through it's options. It may have an option to enable 2 monitors. Good luck.

---

