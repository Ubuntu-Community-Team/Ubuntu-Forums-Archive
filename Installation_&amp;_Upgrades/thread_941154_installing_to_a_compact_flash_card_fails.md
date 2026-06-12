---
title: "installing to a compact flash card fails"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-10-07
I have tried with three CF cards now, all new. I have a generic USB card reader and I unplug my normal hard drive. Initiate a command-line install of Hardy Heron via alternate CD. The installation finishes and then when I reboot, it goes to the grub menu, says it's starting up, then I get something about 'assuming drive cache' twice and it just sits there.

The idea is to install on this machine and then transfer the CF card to an embedded application that does not have a CD drive or USB boot capabilities. This is what I originally did several weeks ago but the machine crashed. I know people install to CF cards and I have done it myself, said embedded application was up and running for weeks until the CF card failed. Now for some reason I can't do the same thing that worked a month ago? With multiple cards?

---

### Post by BetterSense on 2008-10-08
Please help, I'm out a lot of money if this won't work.

---

### Post by gilgongo on 2008-10-12
Have you tried any kernel options on the install? Feels like maybe it's expecting something to be there that isn't - like maybe ATA drivers of some kind?

---

