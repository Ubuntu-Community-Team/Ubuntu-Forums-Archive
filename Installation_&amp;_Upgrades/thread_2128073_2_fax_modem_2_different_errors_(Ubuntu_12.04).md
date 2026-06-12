---
title: "2 fax modem 2 different errors (Ubuntu 12.04)"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by JohanoFiera on 2013-03-22
Hello,

I am using an almost fresh install of Ubuntu 12.04.

The computer has an internal pci fax modem and an external USB fax modem is also connected at the same time.

I used the hsfmodem-7.80.02.06x86_64full drivers to set them up. I had to modify a few files before installing the driver, I followed these instructions: [http://ubuntuforums.org/showthread.php?t=1903439](http://ubuntuforums.org/showthread.php?t=1903439)

After I installed the driver, I had 2 fax modem recognized.

Internal PCI fax modem: ttySHSF0
External USB fax modem ttySHSF1

Now, when I use efax-gtk and try them out (by calling with my mobile phone) I have these problems:

ttySHSF0 - does not pick up the line, instead it start with fax receiving mode immediately (the different beeping sounds a fax makes when sending/receiving).

ttySHSF1 - picks up as it should, but then stays silent  (I can hear nothing on my phone).

I have never setup a modem in Linux before, so I have no clue where to start looking.

Anyone here willing to try to help me troubleshoot this?

---

### Post by JohanoFiera on 2013-03-22
bump

---

