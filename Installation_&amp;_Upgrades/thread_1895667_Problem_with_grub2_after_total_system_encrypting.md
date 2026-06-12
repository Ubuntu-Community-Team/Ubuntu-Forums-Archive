---
title: "Problem with grub2 after total system encrypting"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by den372 on 2011-12-15
Hi I installed 11.04  from the alternate cd and encrypted / part, home part and swap. Everything worked great (thanks for all the help). My question is I tried to install a second encrypted installation of 11.04 on the same disk. Everything worked but when the installation proceeded to the grub2 writing to the master boot record part, the install failed. The system could not write out to the master boot record. I created a 250mb boot part, I assumed that would sufficient. I thought grub2 was smart enough to find earlier entries in the boot part and simply add them to the boot menu. Am I thinking wrong on this or is there perhaps something I have missed in the install. I have all the kernel parameters and correct paths to manually boot from grub2 at boot up, unfortunately grub2 jumps immediately into requesting a pass-phrase for the first encrypted system and never displays the boot menu. Any insight or thoughts on this issue greatly appreciated

---

