---
title: "Problem with Unity after upgrade 12.04 to 12.10"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by ymilev on 2012-11-21
Hello!
Yesterday decided to upgrade my Ubuntu to 12.10 using the update manager - so changed to offer upgrades for every new version (it was on default only for LTS versions) and when offer for 12.10 appeared started the upgrade. Some times it asked me if to reset some personalised files with the new ones and I confirmed all, but preserved the older version for libccid, to spare all the work on configuring again my electronic signature.
Once I cancelled instalation during the download stage becouse of need to travel and continued with downloading from another server ( due to speed problem with the older update server)
It looked like everything finished fine, but when rebooted there was only the desktop with 2 files on it, but without the ribbons leftside (with starters) and upside (with the clock, netwwork symbols and the buttons for preferencies and exit.
Obviously there was a problem with the graphic environment, becouse using ctrl-alt-t I can open terminal and start firefox, or openoffice. I opened screen settings and looked for auto-hide starters, but it was disabled by defaut.
Can you help me fixing this problem? Tried to find anything in the net, but unsuccessfully up to now. So I'm thinking already on deleting the installation and reinstalling 12.04 from disk
Is there a way to preserve installed programs with their settings, so to avoid installing them again? I read for progam APTtoCD, but I have problems with the CD drive, so I'm not sure that will succeed with this program.

---

### Post by Hagar Delest on 2012-11-23
I've also experienced troubles in the past with such upgrades. Now I only install from scratch. I've several partitions, including 2 dedicated to the OS: 1 for the current version and the new flavor on the other one. And other partitions for documents so that nothing is lost. I've also symlinks to secure places for my FF, TB and OpenOffice profiles. The trick is to print the "map" of your HD so that at the install you configure correctly each partition!

---

