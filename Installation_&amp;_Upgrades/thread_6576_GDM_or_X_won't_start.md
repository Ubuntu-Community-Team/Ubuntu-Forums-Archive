---
title: "GDM or X won't start"
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by thebeast on 2004-11-29
I just got my shiny new pressed Ubunut CDs.  Very impressed with the overall presentation.  More than I expected.  But I was severely disappointed when I tried to install it and when I boot into the new Ubuntu system GDM flickers the screen a few times and returns me to the command line!!

I've tried changing resolutions to very conservative levels [800 x 600] and I put in my exact monitor refresh rates through XF86Config.  I've tried a few times to reinstall and the same problems happen.

I have a USB mouse if that helps.  Slack 10 didn't play nice with it.

I'm thinking the Pressed CD might be plain bad.  My live CD said hdc was giving errors in multiple sectors when I tried to boot it.

---

### Post by colnago on 2004-11-30
Try changing the mouse device to  /dev/psaux or whatever you see in /dev that looks like it might be the mouse.  There should be an error about this in ~/.xsession-errors or in /var/log/...

---

### Post by Dennis_k on 2004-11-30
X did'nt start for me too the first time.
Try and reconfigure your xserver using the following command:
sudo dpkg-reconfigure xserver-xfree86

---

### Post by thebeast on 2004-11-30
Ok i'll try it.  I plugged in my PS/2 mouse and reinstalled it and the same exact thing happened tho.

---

