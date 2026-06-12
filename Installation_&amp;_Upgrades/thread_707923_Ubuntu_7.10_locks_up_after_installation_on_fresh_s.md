---
title: "Ubuntu 7.10 locks up after installation on fresh system"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by wonkderboko on 2008-02-25
I just built a fresh system based on the Ars budget setup here: [http://arstechnica.com/guides/buyer/guide-200801.ars/2](http://arstechnica.com/guides/buyer/guide-200801.ars/2)

I followed its recommendations to the T.

Anyway, I downloaded 7.10 and installed it and the install would always lock up.  So then I downloaded the Alternate CD and that installed perfectly.  I booted it up to the terminal and was able to apt-get install successfully and applied all of the current updates.

After installation it will reboot and get to the login screen.  I will login successfully and as soon as it gets to the desktop (with menubar that is accessible) the system will lockup.  No keyboard control, no mouse control.  Dead, Jim.

Any ideas on ways to narrow down this problem?  I am really bummed.  I have used Ubuntu on older hardware without issue so this really grinds me now that I have brand new hardware.  If there is some way to get to some kind of logging console that could narrow down what is dying I would be most appreciative.

thanks for your time
-terry

---

### Post by Sam Lars on 2008-02-25
Is the hardware defective?  I had freezing with a motherboard once and had to send it back.
Is it leaving anything in dmesg or syslog?

---

