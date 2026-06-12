---
title: "Upgrading from 8.10 to ??"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by johnhdsi on 2009-11-25
Quick question for everyone out there. I have an older ATI 9200SE vid card and I have been thinking about upgrading my system from 8.10 to 9.04 or 9.10 so I can be more up to date with everything. My question is in regards to the vid card, will the ATI card work "out of the box" sorta speak like in 8.10 or do you need to get new drivers for it, and if so then where would I get them?

Another quick question in regards to wireless and 9.04 and 9.1, I have a pc at work that runs XP and I would like to dual boot with Ubuntu for various reasons, my main issue here has always been my wireless card. I have a Belkin F5D8001 card that works well in XP but I Tried geting it to work in 8.10 to no avail. Does 9.04-9.10 support wireless better now? I tried the ndiswrapper fix but never got it o work. 

Any suggestions or input would be greatly appreciated, thanks in advance!!!!

John

---

### Post by Mark Phelps on 2009-11-25
> **johnhdsi said:**
> Quick question for everyone out there. I have an older ATI 9200SE vid card and I have been thinking about upgrading my system from 8.10 to 9.04 or 9.10 so I can be more up to date with everything. My question is in regards to the vid card, will the ATI card work "out of the box" sorta speak like in 8.10 or do you need to get new drivers for it, and if so then where would I get them?.

Unfortunately, ATI dropped support for your card (and lots of others) earlier this year, so there are no ATI drivers that will work with your card and Ubuntu versions newer than 8.10.

However, the open source driver SHOULD work and will be installed automatically when you do the installation.

But, before you do an upgrade, be sure to REMOVE the ATI driver and replace it with the open source; otherwise, you run the risk of having no graphics when you finish the upgrade.

Link with instructions:  [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by johnhdsi on 2009-11-25
Thank you very much I appreciate the help.

Any ideas on the wireless? I would really like to load Ubunu on my work pc also but the wireless is my only hang up.

---

