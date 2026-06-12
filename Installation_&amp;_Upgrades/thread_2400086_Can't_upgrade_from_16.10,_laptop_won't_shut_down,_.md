---
title: "Can't upgrade from 16.10, laptop won't shut down, CAPS lock blinking, not booting"
date: 2018-09-02
forum: Installation &amp; Upgrades
---

### Post by simon-hegener on 2018-09-02
Hey guys,

My laptop (HP ProBook 4540S, originally with SUSE 11) is driving me nuts. I installed Ubuntu a few years ago and always got the updates. Since 16.10 I can't upgrade anymore and it shows an error "not all updates can be installed". But even a partial upgrade won't work.

Plus, when I shut down the laptop turns itself off after shutting down and after a few seconds turns itself on again. I can only click the power button to turn it off at that moment to keep it turned off. 

Sometimes, when I start the laptop, it just doesn't start properly: the CAPS lock key blinks and the ventilation is going like crazy. Then I can't use the power button but I have to remove the battery to turn it off. 

Does anyone know what to do? I'm guessing this is a bigger issue and I would love to bring my device somewhere to have it checked. Is there something like that in the area of Zurich, Switzerland?


Cheers and I highly appreciate all feedback!

Simon
Ah, and another thing: at one point my laptop inverted the scrolling direction of my mouse pad. Can I revert that?

---

### Post by TheFu on 2018-09-02
Support for non-LTS releases lasts 6-9 months. 16.10 support ended around June of 2017.  No 17.xx releases are currently supported.  I only install LTS releases to avoid only having a version for 6months before being forced to upgrade.  16.04 and 18.04 are both LTS with either 3 or 5 yrs of support, depending on which flavor you install.
[https://www.ubuntu.com/about/release-cycle](https://www.ubuntu.com/about/release-cycle) tries to explain the release cycle and process.

Yes, you probably have hardware issues.  Check the system logs for errors and warnings.  You can google "ubuntu log files" to find a guide about that. Look for results that have ubuntu.com in the domain of the URL.

After you see the logs, the problem hardware they point at should be reseated or changed. Hard to say what that will be.  Or you can take the computer into any computer shop and have them run hardware diagnostics. I'd call ahead to ensure they are comfortable with Ubuntu as the OS.  In my part of the world, the diagnostic charge is US$50-$100. 

I would also try using a fresh USB flash boot and see if the problem doesn't stop. If it does, then it is something in your installation or in the storage subsystem.

---

### Post by simon-hegener on 2018-09-23
Thanks a lot for your reply!

---

