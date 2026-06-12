---
title: "Ubuntu 10.4-64bit Install Nvidia Dispay not working on 1st boot"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by mutineer612 on 2010-04-30
After installing using the 10.4 Alternate CD I was unable to login after rebooting.  I was able to see the cursor, and the purple background but no login prompt.  

In my situation using and HP ML-310 G4 64bit Intel Pentium-D, with an Nvidia video adapter I discovered my problem was a video issue.  I rebooted and held down the shift key during boot after reading that grub2 used shift instead of the escape key.  I then booted in recovery mode and selected the lower graphics option.  

I was now able to login to 10.4 for the first time, and I went and installed the 'Recommended' restricted driver for the Nvidia card and rebooted once more without holding shift.   

Other than this issue at first boot everything else is working as expected. Hopefully this helps others avoid the same issue.

---

