---
title: "Incorporating restricte modules (e.g. video drivers) into new kernel versions"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by brm on 2010-03-29
Which script (or which package) is responsible for managing the integration of restricted modules into new kernels?

For the last several versions of Ku/Ubuntu, a script runs whenever an upgrade downloads a kernel update. This script ensures that the correct linux-headers packages are also downloaded, it calls dkms and incorporates restricted modules into the new kernel version. In my case, as well as that of many other users, the module involved is the proprietary nVidia module.

A regression occurred at or about the time of the release of the Lucid Lynx beta. This script no longer runs. Boots with the new kernels fail because the proprietary module is not loaded properly.

I wish to file a bug against the package containing this script? Can anyone help me determine which package?

---

