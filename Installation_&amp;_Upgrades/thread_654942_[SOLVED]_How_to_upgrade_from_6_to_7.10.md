---
title: "[SOLVED] How to upgrade from 6 to 7.10"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by sieg on 2007-12-31
What are the network upgrade rules? I'm trying to follow the directions at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) but they seem to indicate one can only upgrade from 7.04 to 7.10.

The problem is that I'm so old I don't have an "Upgrade" button on my Update manager. So I followed the directions on the sticky thread where it said 'gksu "upgrade-manager -c" and now I see a button that says I can upgrade to 6.10!

I wonder what I was running. I tried the menu entry "about ubuntu" and it did not seem to have a version number there! uname -a says 2.6.15.29-386. What version of ubuntu does that translate to?

So anyway, how do I upgrade to 7.10 from 6.10? I hope I don't have to do a new install because it took several linux engineers 3 hours at the Linux User's Group Install festival to figure out how to configure my CUPS/HP85 printer drivers.

Thanks,
Siegfried

---

### Post by overdrank on 2007-12-31
> **sieg said:**
> What are the network upgrade rules? I'm trying to follow the directions at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) but they seem to indicate one can only upgrade from 7.04 to 7.10.

The problem is that I'm so old I don't have an "Upgrade" button on my Update manager. So I followed the directions on the sticky thread where it said 'gksu "upgrade-manager -c" and now I see a button that says I can upgrade to 6.10!

I wonder what I was running. I tried the menu entry "about ubuntu" and it did not seem to have a version number there! uname -a says 2.6.15.29-386. What version of ubuntu does that translate to?

So anyway, how do I upgrade to 7.10 from 6.10? I hope I don't have to do a new install because it took several linux engineers 3 hours at the Linux User's Group Install festival to figure out how to configure my CUPS/HP85 printer drivers.

Thanks,
Siegfried

HI if it is notifying you that 6.10 is available the chances are you are using 6.06. You can verify this with the command ```
lsb_release -a 
``` If this is the case you can upgrade to the next version 6.10 and then 7.04 and finally 7.10. This will be very time consuming and likely to cause errors on your system in my opinion. You may be able to search for you printer and maybe the support is better in 7.10 Gutsy. Good luck!

---

### Post by wh0rd on 2007-12-31
At this point there is no jump from 6.10 to 7.10. You'll have to upgrade from version to version until you get the current version. So that means 6.10 to 7.04 to 7.10.

Just curious why not do a fresh install instead? A lot has changed since 6.10. You might to research the current state of your printer.

---

