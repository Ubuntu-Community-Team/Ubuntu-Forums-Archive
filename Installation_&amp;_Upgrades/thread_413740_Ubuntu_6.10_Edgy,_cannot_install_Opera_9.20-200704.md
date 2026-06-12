---
title: "Ubuntu 6.10 Edgy, cannot install Opera 9.20-20070409.6ubuntu2 -&gt; wrong package?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by evaarties on 2007-04-19
I got a message from the update-manager there was an update for Opera (I was running 9.10). So I looked and saw this one:

9.20-20070409.6ubuntu2 (edgy-commercial)

However, I cannot install this one because:

opera:
  Depends on:libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends on:libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends on:libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
  Depends on:libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed


Does this mean the package isn't correct for Edgy Eft?

NB I did managed to download and install the Ubuntu package from Opera directly, I now have a plain 9.20-20070409 installed. The update however is still showing in the update-manager.



PS This person is having the same simptons: [http://ubuntuforums.org/showthread.php?t=413620](http://ubuntuforums.org/showthread.php?t=413620)

---

