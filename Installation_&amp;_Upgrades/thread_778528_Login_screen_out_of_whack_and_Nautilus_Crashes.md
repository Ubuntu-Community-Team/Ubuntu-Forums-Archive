---
title: "Login screen out of whack and Nautilus Crashes"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2008-05-02
Hello Everyone,

I have Hardy on my laptop having installed it from beta and followed through the updates to the stable release. I waited until now to upgrade from Gutsy to Hardy on my desktop because more important work is done there.  I upgraded through the Update Manager and all seemed to go well.  At the first reboot I found that I had display issues even though I had the Nvidia drivers installed, but I had stupidly forgot to change the Grub boot menu to boot the new kernel and I was booting Hardy with Gutsy's kernel.  That was fixed.  However, I now have two issues that I can't seem to resolve and I was hoping someone would know the answer.

First, the login screen is at the correct resolution, but is well off center.  The right side of the screen is black and the login window is off center, preventing me from seeing the options at the bottom of the screen.  Oddly, as soon as I login, it corrects itself to a correct screen.  

Secondly, the update manager GUI crashes nautilus and this can't be corrected without a reboot.  I get the error message that nautilus can't be used because of bonobo.  I can still access the top and bottom panel, but get a black screen.  Now, I have seen a number of threads from people with this same issue and it seems to be related to an old version of mono being leftover from Gutsy during the upgrade.  However, I seem to have the latest version of mono installed (1.2.6) according to synaptic.  I can still update through the terminal with apt-get, but this is an irritating issue.

If anyone knows a fix to these two issues, I would certainly appreciate the help.

Thanks in advance

Bob

---

### Post by bobnutfield on 2008-05-02
Well, at least one issue was solved with some more intense googling.  It turns out that my xorg.conf file had a wrong first entry for the screen resolution.  The login window apparently gets its resolution from the first entry in the mode line of the "screen" entry.  Mine was set at 1280X960 when the correct resolution should have been 1280X1024.  This corrected the login window issues.  Hope this helps someone else.

Bob

---

