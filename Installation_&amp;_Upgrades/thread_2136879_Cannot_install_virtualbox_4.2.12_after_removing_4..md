---
title: "Cannot install virtualbox 4.2.12 after removing 4.1.12"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by voipster on 2013-04-18
First I would like to thank any/all for their input on this. I have been at this for hours! 

   I have Ubuntu 12.04 AMD64 and was trying to upgrade virtualbox 4.1.12 to 4.2.12 package: ("virtualbox-4.2_4.2.12-84980~Ubuntu~precise_amd64.deb") I removed 4.1.12 with Ubuntu software center. Then tried to install 4.2.12. got "**Error: Conflicts with the installed package 'virtualbox-guest-additions-iso'**" then tried removing with synaptic. got two more packages removed. Tried installing again. Same error. Searched from root filesystem for anything including "*virtual*". Found 7 more items. tracked the down and "rm"d them all. search now returns nothing including "*virtual*". Retry installation of 4.2.12 with software center and gdebi. Both return with  "**Error: Conflicts with the installed package 'virtualbox-guest-additions-iso'**" I have sought out every piece of 4.1.12 that I can find and wiped it out.  

Any help on this will be greatly appreciated.

Thank you

---

### Post by voipster on 2013-04-22
Well, I now have removed virtualbox 4.1.12 with Aptitude. However it also removed Netflix desktop, Skype and all the programs I had in "Play on Linux". I have installed Virtualbox 4.2.12 it is working well. I have retrieved the programs I wanted. And all is working well.

---

