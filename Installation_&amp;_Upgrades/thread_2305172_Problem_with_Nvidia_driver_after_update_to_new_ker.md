---
title: "Problem with Nvidia driver after update to new kernel"
date: 2015-12-03
forum: Installation &amp; Upgrades
---

### Post by arthur-diemel on 2015-12-03
EDIT: Problem is solved after deleting all nvidia packages(except the one linked to ubuntu-desktop) through synaptic. Computer restarted in 640x480 and I was able to succesfully install the 304-postrelease-updates driver.

Today I got an update for the new drivers, 3.13.0-71. Installation had a little problem, apparently every 5 kernels my kernel-folder needs cleaning. Got everything up and running again, but the Nvidia drivers wont install/activate anymore. I get a message about looking in /var/log/jockey.log when I try it. In the list, only Nvidia driver 304 and 304-updates are listed, where before my kernel update I was using a newer version (310 I think). I have reinstalled nvidia-updates like one of the ask ubuntu topics suggested, but it is not working. Log was as follows:
..

Unable to post the full log file, since I get a message that it has 38 images in it and the max is 8. I thought there would be none images in the log.. I have been busy with it for a fiew hour now, anyone knows what to do? First, a lot more nvidia drivers were listed(one more, with the post release updates available as choice as well. Does anyone know how I can fix this? I'm working with a big black bars on all four sides of the screen now since the non-driver isn't able to use full screen.

Thanks in advance,
Arthur

---

### Post by arthur-diemel on 2015-12-03
In the log, this line > 2015-12-03 16:14:04,423 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates comes up while trying to install the driver.

---

