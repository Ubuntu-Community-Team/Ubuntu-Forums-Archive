---
title: "Ubuntu won't go past splash screen, screen just turns blank"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by shortman101n on 2010-07-25
I have tried installing Ubuntu 9.10 on another computer, however the regular installer never worked.  It would go to the loading screen with the ubuntu logo and the dots that would change color to show it is loading, but would never go further than that.  I then used the text-based installer to install it.  It said everything installed fine, but it still doesn't go past the basic ubuntu logo.  I turned off the quiet option before booting, and it always gets stuck after it says "Starting AppArmor profiles", then it just sits there.  Its a 2.6ghz pentium 4 with 2gb of ram.  Ask any questions you need for clarification and throw out any suggestions, I'm willing to try anything.

---

### Post by MAFoElffen on 2010-07-25
What is your hardware- especially the video card, mouse and monitor?  (or any game controller that might be connected)

---

### Post by shortman101n on 2010-07-25
Since there is no bootable operating system, and no info in the BIOS about the video card I looked up the specs online and it appears to be an Intel Intergrated graphics card, I assume the Intel 845 G/GL Integrated Video series.  The Keyboard is a regular dell keyboard with a ps2 connection, and a HP usb mouse.  Nothing wireless.

---

### Post by shortman101n on 2010-07-26
I fixed it, all I had to do was remove the wireless pci card.

---

### Post by aextance on 2010-08-14
I think I have something similar going on. My graphics card is an ATI Radeon Mobility 7500. My laptop works fine on its own, but I normally use it as my main work machine via a docking station. When I do that it hangs on the splash screen.

Interestingly this has happened since I upgraded my kernel to 2.6.35. I know that there are issues with Radeon graphics cards and Ubuntu. I had actually upgraded the kernel to try and get round an issue where going through the docking station into a monitor messed with the contrast, brightness and gamma, which is I think what these guys had:

[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/548709](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/548709)

Likewise, then, the laptop screen itself was fine. Any suggestions?

---

