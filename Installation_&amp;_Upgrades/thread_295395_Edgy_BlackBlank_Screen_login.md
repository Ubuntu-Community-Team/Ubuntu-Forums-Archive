---
title: "Edgy Black/Blank Screen login"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by itly on 2006-11-08
Registered purely to post solution.

Previously ran dual monitors in Dapper (nvidia card)

Upgraded to Edgy via apt

Had similar difficulties to number of people with blank screen instead of login screen after splash.

Tried re-installing X-server etc.

Finally worked after re-installing nvidia-glx drivers.

(sudo apt-get install nvidia-glx)

This worked by accident - attempting to follow someonelse's solution by installing fglrx drivers (which did not work) and was simply re-installing nvidia-glx to go back to original settings to try something else.

and hey... it booted.

Good luck. Have used the forums for a number of years and never had to post a question - if you look hard enough someone else is having the same trouble somewhere. Thanks to all those who take the time to give detailed answers.

---

### Post by daller on 2006-11-08
It's a common bug in twinview.

Use 2 X-Screens instead:

[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

---

