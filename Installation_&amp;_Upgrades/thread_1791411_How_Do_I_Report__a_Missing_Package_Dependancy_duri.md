---
title: "How Do I Report  a Missing Package Dependancy during an upgrade?"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by crasic on 2011-06-26
A friend of mine (somewhat new to linux) recently upgraded from 10.10  to 11.04 and his OS broke from the upgrade. A few minutes of  troubleshooting showed that the culprit was the PAE kernel that the  upgrade decided to install since it determined he had 4GB of physical  RAM (I wasn't present during the upgrade so I'm not sure whether it asked him or not). More specifically the upgrade forgot to install the linux-headers-generic-pae required by the closed source nvidia drivers. 



I'm not entirely sure how to report this bug to the devs. Its an easy  fix (after booting into the non-pae kernel and installing the package  everything worked), but they are encouraging users to use the built-in  bug reporting system and I'm not entirely certain how to report update  bugs. 



*NOTE* Posted first on [askubuntu.com]("http://askubuntu.com/questions/42803/how-do-i-report-a-missing-package-dependency-during-an-upgrade") (the ubuntu stackexchange forum) with no answer for 5 weeks. I will crosspost any answer here on askubuntu unless the post author asks me not too.

*SECOND NOTE* This is for Vanilla Ubuntu, but thread marked all variants since the primary question (reporting upgrade bugs) applies to all.

---

### Post by Toz on 2011-06-26
I ran into this myself. A bug report for this already exists. See: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/710744]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/710744"), though its unclear what, if anything, is being done about it.

And for information on how to report bugs, have a look at: [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

