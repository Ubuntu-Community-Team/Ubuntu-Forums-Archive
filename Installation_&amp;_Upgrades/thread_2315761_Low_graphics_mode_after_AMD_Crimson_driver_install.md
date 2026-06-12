---
title: "Low graphics mode after AMD Crimson driver install"
date: 2016-03-02
forum: Installation &amp; Upgrades
---

### Post by Ubbly on 2016-03-02
SHORT VERSION - please, how do I install the latest AMD drivers for 14.04.4 LTS ?

---

### Post by mastablasta on 2016-03-02
first - what is your GPU chip? - [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by grahammechanical on 2016-03-02
Usually we let Additional Drivers do it. The drivers available in Additional Drivers are the "latest" safe drivers as far as the Ubuntu maintainers are concerned. If we want or need newer drivers than those and we have an AMD video adapter then we have one option. Download from the AMD website and install by hand.

If we have an Nvidia video adapter then we have 2 options. Download from the Nvidia web site or install this PPA.

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Regards

---

### Post by Ubbly on 2016-03-02
In reply - I did have a detailed post but couldn't get it to format properly into paragraphs. Anyway. It's ubuntu 14.04.4 LTS and HD5850. They nearest HD5xxx series package on AMD website is for 14.04.2 LTS so I tried that. Opened the deb package with software centre and ignored the bad quality warning. Ran aticonfig after it installed, then rebooted. Probably did lots of things I shouldn't do ? Anyway, I take the point about using the additional drivers so I did go back to that in the end and it works just fine. I just wanted the latest and greatest thing and the new control interface

---

### Post by X-RED_Tech on 2016-03-03
The latest isn't always the greatest.
Graphics drivers are often tricky in Linux therefore you should use what works in your system.
Newer versions most of the times only add support for newer hardware. It doesn't necessarily improve anything for the card you already have.

---

### Post by Ubbly on 2016-03-04
Ahh... OK good points, that settles it.

---

