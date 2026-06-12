---
title: "Mouse not reacting. VMWare Fusion MacOs"
date: 2018-10-07
forum: Installation &amp; Upgrades
---

### Post by jmverreault on 2018-10-07
I am trying to install Ubuntu as a virtual machine using VMWare Fusion 10.1.3 on MacOS.
After my 1st trial it got stuck at Scanning Disks ... after 100% of the progress bar.
The vmware-vmx was at 100% for a long time and it never completed the Scanning Disks.

So I gave up, deleted the vmware VM file and started all over using the following guideline:
[http://www.xfiles.dk/guide-on-how-to-install-ubuntu-on-vmware-fusion/](http://www.xfiles.dk/guide-on-how-to-install-ubuntu-on-vmware-fusion/)

After following that guidelines Ubuntu install went further.
Currently it is at step Keyboard Layout  (see attached snapshot)
But at this stage when I click my mouse cursor into the VM Ubuntu window nothing happens.
It it as if there were no functioning mouse in the VM window.

Any ideas on what could cause this ?

Thanks

JM[ATTACH=CONFIG]281277[/ATTACH]

---

### Post by jmverreault on 2018-10-07
Resolved. 
Changed 1 Processor to 2 and increased Memory from 1024MB to 2048MB in Virtual Machine Settings.
From there on it stopped freezing.

---

