---
title: "Problems re Ubuntu 14.04 Upgrade"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by russell boyce on 2014-06-03
I upgraded from 13.10 to 14.04 as suggested on the update screen in 13.10 on both my machines running Nvidea Gforce 6150 cards they both lost the graphics and had to have the video drivers installed yet again! When I use my dual boot machine it does not always cleanly boot to the desktop sometimes losing the desktop just after loading, also now I am running 14.04 I get daily and sometimes more fequent notifications that 14.04 has experienced a problem. I also find that programs such a Gthumb which always worked perfectly now crash as does glabels and planner. Decidedly upset by the performance. Was previously a great fan of Ubuntu but not sure any more it feels nearly as bad as Windows at least that doesn't lose my graphics and all my printers whenever I upgrade!

---

### Post by mörgæs on 2014-06-03
The upgrade is likely to be the problem, not 14.04 in itself. 
Save yourself trouble, always a fresh install.

---

### Post by monkeybrain20122 on 2014-06-03
You have to remove your Nvidia driver first before you upgrade. In general "upgrade" is not a robust process and you have to revert your system to a pristine state before upgrading for it to have a chance to succeed (no proprietary driver, no ppa, no third party applications and other tweaking/changing of system configurations..). 

The update-manager's upgrade prompt should be disabled as it tempts people to upgrade on impulse by just pressing a button  out of the blue and once the process starts there is no way to abort it without breaking your system (and it will take hours whether it works or not) It is a very poor design to have it just pop up to insinuate you to "press me" without informing you about the process and the preparations and without giving you a chance to even back up your data.

+1 to back up your data and do a clean install. It takes 15 minutes, probably less time than you need to restore your system to pristine state in preparation for "upgrade" and it takes another 20 minutes or so to reinstall all your software (unless you compile , but in that case they won't survive "upgrade" any way). Forget about "upgrade".

---

