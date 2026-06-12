---
title: "&quot;Could not calculate the upgrade&quot; - upgrading Ubuntu 14.04 to 16.04"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by Edward_Fish on 2016-09-20
Ubuntu has been nagging me to upgrade to 16.04 (from 14.04) for some time now. After starting my computer today (HP Pavilion 1000 laptop) I was prompted yet again. I had backed up my files the day before so I chose to do it. The release notes window opened, I clicked the button to continue. I was then presented with a list of steps and a progress bar.
After a moment I saw a screen saying: "Third party sources disabled"
[http://postimg.org/image/6nn4sgsj9/](http://postimg.org/image/6nn4sgsj9/)
It didn't seem to be anything serious, so I closed it and let the updater move on. Soon, I saw an error icon in the top-right panel. "An error occurred, please run Package Manager [etc]". This was worrying.
[http://postimg.org/image/l9j2f1med/](http://postimg.org/image/l9j2f1med/)
Finally, this error message appeared, "Could not calculate the upgrade". After that, the upgrader reverted the changes and closed itself.
[http://postimg.org/image/yyn1r53hh/](http://postimg.org/image/yyn1r53hh/)
Running any of these 4 commands: *apt-get, sudo apt-get, sudo apt-get install, sudo apt-get install* did not say anything out of the ordinary. Opening Synaptic Package Manager did not do anything unusual. There was also nothing relevant to be found in */var/log/dpkg.log*. So:
1) Is upgrading worth the fuss?
2) If so, what do I do?
I will be happy to run any suggested commands and post their output.

---

