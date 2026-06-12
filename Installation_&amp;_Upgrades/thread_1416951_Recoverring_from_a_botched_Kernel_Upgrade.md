---
title: "Recoverring from a botched Kernel Upgrade"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by MS-Hater on 2010-02-26
I admit, my knowledge of LINUX isn't that great. That said, I thought I'd be able to pull off a basic upgrade (clean install of a whole new kernel, not patching the existing one) from the latest 2.6.31 in the ubuntu repo (I think it's 2.6.31-19.54 to be exact) to 2.6.33 (kernel --latest-stable) from source. I got all the config done, compiled it, and updated GRUB, rebooted to find that it had a "2.6.33.old" entry in the menu (not particularly relevant, I admit) even though I only ran the "make install" command once. Anyway, when I selected the non-old entry, it churned for a moment, gave a couple of weird screens for <1 sec each, and then gave me an error about a missing graphics module (I'll look for how to automate loading modules on my own, and see if I can port the existing NVIDIA module from my working kernel to the newer one) and gave me a list of options like "boot into graphics safe-mode" "boot to login shell", etc. and the mouse wouldn't work, so I had to use the keyboard to work the screen (i chose the shell login, since I didn't feel like seeing ubuntu's butchered face while it's in "graphics safe-mode"). I managed to get the computer to boot into the stock kernel, and am now wondering  the following:

1). Do any of you guys out there think it's worth trying to save this kernel update?
2). How do I go about removing the "2.6.33.old" kernel & entry? (i've tried synaptec, the "make remove" and "make auto-remove" commands with no success.)

Any help is greatly appreciated.

Jacob.

---

### Post by MS-Hater on 2010-03-04
Bump.

---

