---
title: "Windows doesn't even try to boot after Grub"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by aodestruction on 2010-01-01
So, I convinced my family to switch to xUbuntu about six months ago, and setup a dual boot with Windows. After the first boot, I tried to boot XP with great success, and I let it be. Unfortunately, in the intervening months XP's boot status has gone kuput. After a few trials, and tribulations (thought I lost the partition table for a moment there) I was able to get the Grub boot menu back again, and xUbuntu loads just fine as it did before. However, I'm still stuck with the same problem when I try to load Windows: I get the Grub "Starting..." screen, and nothing after that. 

   The Windows Install CD is less than helpful, unfortunately. There seem to be a grand total of four options, and none of them seem to work. I have done the "Install Windows" bit, and asked it to repair the installation; I have run the >FIXBOOT command in the recovery consol with absolutely no effect (the same goes for the >BOOTCFG \rebuild command); the >FIXMBR command from the recovery console succeeded only in removing grub, but instead of loading Windows as one might expect, the system would hang after trying to boot from the hard-disk. (Thankfully, grub reinstalls easily enough though).

   There is a program called MBRFix (different from the recovery consol FIXMBR command) which might be able to help, but it is a Windows executable, and I can't seem to get it to run under dosemu (just a very fast opening and closing of a terminal there), or my not-as-handy-as-I-thought-it-would-be freeDOS live CD. The painfully (almost humorously) ironic thing is that if it were possible to boot windows, I wouldn't need the program in the first place...

   Oh, and I've also tried the RIPLinux boot disk, but when grub tries to load Windows from that, I am sent to the XP installation screen (it says that Windows is ready to install, and asks me to insert the installation CD). First off, WTF is up with that anyhow? And second, I am trying NOT to overwrite the installation because it contains a program needed by my parents, and I may or may not have lost the CD for that one...


Thanks for all of your potential help! And happy New Year!

---

### Post by haribol707 on 2010-01-02
Did 'Repair/recover' option with your XP CD report anything?

---

