---
title: "ATI Mobility Radeon HD 3200 in trouble after last upgrade"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by spitzer on 2010-01-06
A new Ubuntu update became available this morning which I dutifully
installed. However on restart I got a message "Failed to load module
"ati" (module does not exist, 0). And then "Ubuntu is running in low
graphics mode" which in reality meant that each of my two screens(the other one is a ViewSonic) were
mirrors of each other! I rummaged around the Net with Google with not
much joy and eventually downloaded the appropriate driver package from
AMD ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English&rev=9.12&ostype=](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English&rev=9.12&ostype=)) - registration required. This got rid of the error messages, but still duplicate screens -
then I looked at the ATI Catalyst Control Center and found a Xinerama
option which when activated returned the situation to normal i.e twin screens and being able to move between them.

---

