---
title: "upgrade to 7.04 broke Xwindows"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by pauln600 on 2007-09-27
Upgrading to 7.04 broke my Xwindows - the log file is at

[http://www.picolist.org/Xorg.0.log](http://www.picolist.org/Xorg.0.log)

I haven't installed any proprietary drivers. A copy
of /etc/X11/xorg.conf is at

[http://www.picolist.org/xorg.conf](http://www.picolist.org/xorg.conf)

Tried to recover via dpkg-reconfigure xserver-xorg, which worked
the last time this happened (which was just a couple of weeks
ago as a result of an upgrade to 6.10), but no joy.

Any ideas?

Thanks,
Paul N.

---

### Post by Pumalite on 2007-09-27
What video card do you have and what controllers for it you had?

---

### Post by pauln600 on 2007-09-27
> **Pumalite said:**
> What video card do you have and what controllers for it you had?

It's an ASUS M2V-TVM motherboard with integrated VIA DeltaChrome Graphics Uniit - nothing
else added in hardware or software.

Paul N.

---

### Post by Pumalite on 2007-09-27
Let's try to reconf xserver
Ctrl+Alt+F1 to get a command line
At the command line:
sudo dpkg-reconfigure xserver-xorg. accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by pauln600 on 2007-09-28
> **Pumalite said:**
> Let's try to reconf xserver
Ctrl+Alt+F1 to get a command line
At the command line:
sudo dpkg-reconfigure xserver-xorg. accept most defaults, choose 'vesa' as the driver, then: startx

Changing the driver from 'via' to 'vesa' in xorg.conf works.
Isn't that a little strange, in this case?

Thanks,
Paul N.

---

### Post by Pumalite on 2007-09-28
You are welcome. It's not strange: vesa is a 'generic' driver.

---

