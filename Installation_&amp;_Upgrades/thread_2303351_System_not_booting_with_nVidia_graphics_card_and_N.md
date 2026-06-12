---
title: "System not booting with nVidia graphics card and NOMODESET in grub"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by Sparks27 on 2015-11-18
Installed Linux Ubuntu 14.04.3 LTS
Booted to black screen
Probably cause of NVidia Graphics Card
Tried to boot replacing quiet splash with nomodeset in the grub menu and then:

  [IMG]http://i.stack.imgur.com/FbOy7.jpg[/IMG]
  Nomodeset mode boots to another dead end. This adding swap thing lasts for a couple of minutes and then goes to black screen.
  What can I do to resolve this?

---

### Post by grahammechanical on 2015-11-18
Some information about the hardware would be useful. Does the live session load and run? Did you install and tick the box "Install third party software?" That will install some free but proprietary audio & video codecs and a proprietary video driver. You could try install without ticking the box "Install third party software" and avoid the Nvidia driver until you get to a working desktop.

Not enough information about the machine and what is on  it to even guess a solution.

Regards.

---

