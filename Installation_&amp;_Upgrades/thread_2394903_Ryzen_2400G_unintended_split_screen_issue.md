---
title: "Ryzen 2400G unintended split screen issue"
date: 2018-06-23
forum: Installation &amp; Upgrades
---

### Post by dinkidonk on 2018-06-23
Hello,

I'm trying to install Kubuntu 18.04 on a system with "ASUS PRIME A320M-A" motherboard (BIOS V. 4011) and "Ryzen 5 2400G" APU, using the built-in graphics. When I load Kubuntu from the flash drive, the screen is split down the middle; the left half is OK whereas the right side is a teared copy of the left side. When I move the mouse around from one half to the other half (eg. dragging windows) the screen flickers horribly. Basically the same as here: [https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)

As far as I can figure out I need kernel >= 4.17 and MESA >= 18.2, but how do I manage to get this when it is impossible to install with the issue present? Is is possible to somehow modify the Kubuntu 18.04 ISO to feature the newer kernel+MESA? Are there any information about when an updated ISO will be available?

Thanks in advance! :)

---

### Post by kurt18947 on 2018-06-23
I'm paying attention to these threads because I have an older desktop machine that may need replacing soon and I'm an AMD fan. If I were faced with this problem I'd install a video card and set the BIOS to use it rather than the onboard video. That should take the Ryzen's video out of the picture and may allow installation. If you can get a functioning install you can then update the kernel and mesa versions. That's my thought, whether it would work or not is another matter. I have a much older motherboard/processor and can select either onboard video or PCIe. Your motherboard book/website should tell you whether this option is available to you. If you do try this please let us know what did or didn't work.

---

### Post by dinkidonk on 2018-06-24
I do not have a graphics card and I picked the 2400G because it has one built in. Should have spent more time investigating compatibility with Linux because it seems like 2400G is a bad pick, and a 320 chipset isn't helping either. I can only hope that Linux support will improve soon or else I've wasted good money on a useless upgrade. For now I would not recommend anyone to get a 2400G for a Linux build.

---

### Post by kurt18947 on 2018-06-24
If you're so inclined, you can pick up a not-state-of-the-art video card on Ebay for cheap. I'm running a Dell AMD/ATI card that I paid less than $10 free shipping. I'm assuming a separate video card would take the Ryzen video out of the loop, I don't know that for sure. As you've found out, bleeding edge hardware and Ubuntu or other linux distros may not be happy together. For others reading this thread, Ryzen processors can be purchased with or without integrated graphics. The ones with integrated graphics have model numbers ending in G as dinkidonk's processor does.

Update: Here's a thread in Phoronix about Ryzen 2200G issues.
[https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/1032693-ryzen-2200g-still-not-reliable-in-4-18rc2-when-will-it-work](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/1032693-ryzen-2200g-still-not-reliable-in-4-18rc2-when-will-it-work)

---

