---
title: "upgrade simply just does not start"
date: 2016-08-01
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2016-08-01
Hello fellow ubunters:)
I confess to not being very patient. I just have tried at least five times to upgrade from 14.04 to 16.04  and this ****ing upgrade simply does not start. You get three options on the screen : no, remind me later and yes. 
Since it would not start, I have tried rebooting, I have seen the selfsame options pop up, I have answered yes five times and still nothing, nada, nulla, rien.
But, with the laptop, the upgrade went on very smoothly. 
Could it be this new upgrade is incompatible with an old HP DD7700?

Thanks in advance to anyone with the answer or the 'how to'. 
Chris.

---

### Post by christon74 on 2016-08-01
Problem solved! But for other fellow ubunters like me who wonder how to upgrade from 14.04 to 16.04 and who just like me see that the upgrade does not start when you click 'Yes, upgrade' here is the solution:
open a terminal, and copy-paste this command line:
sudo update-manager -d

Have a nice Monday all of you:)

---

### Post by mörgæs on 2016-08-03
Yes, when possible always use the command line and not the GUI. It often gives a more detailed error message which can be used for troubleshooting.

Remember that the **-d** switch upgrades to the development version, which is 16.10 for now.

---

