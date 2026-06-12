---
title: "Broadcom STA Driver must be reactivated each time to connect"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Donalb on 2009-11-17
Hey all,


Firstly: I've had a look through some of the other Broadcom/Wireless issues before posting.

All networking was fine in 8.10 for the last year and nothing had to done to make it work (ethernet, wireless & 3G). I skipped 9.04.
First week with Karmic I was just using ethernet. 

After a fresh install, while visiting my ill mother last week I realised the wireless wasn't working.

I installed the two suggested Broadcom Drivers, (STA & B43).

Activating B43 didn't work, but STA did.

However the next time I restarted, STA was still activated but wireless wasn't working.
After some fiddling around I realised I had to activate B43A, (which did nothing), then reactivate STA.
This situation has continued.
STA only works if I activate B43A first, <then> (re-)activate STA.
(BTW, sometimes doing this crashes the laptop to power-off state.)

My Broadcom is BCM4322 which, I've read doesn't have a specific driver but the legacy should run it. Recall it's worked fine for the last year. 

The wireless button state seems also to make no difference (to enabling wireless).

Any ideas or suggestions?

Regards

---

### Post by benbelly on 2009-11-28
I have a similar problem after upgrading from Jaunty to Karmic on Wednesday.  I only have the STA driver, and I need to deactivate (remove) it and reactivate it to in order to connect to use it.

Also, once I have reactivated the driver, but before I connect to a network, if I try to use the network my system locks up completely.  I can't say with 100% certainty that the network access causes the problem - it could just be an aftereffect of activating the STA driver.

Help?

Thanks,
-Ben

---

### Post by lommol on 2009-12-20
I too have the exact same problem as [Donalb]("http://ubuntuforums.org/member.php?u=376184"),  Has there been any progress?  Having to manually deactivate the Broadcom STA driver and reactivate it every time I start Ubuntu is irritating.

---

### Post by benbelly on 2009-12-20
I have switched to wicd for network management and ndiswrapper and windows drivers, and everything seems to work now.  Lousy solution though.  I have had enough trouble with this upgrade that I'm looking at other distros.

---

