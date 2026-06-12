---
title: "apt-get searching for non existing packages"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by ildella on 2006-10-11
This morning my up-to-date Edgy Eft propose me a long list of updates via the Update Manager. I did those updates. 
Unfortunately the OS freezed during the update, at the restart nvidia driver was broken (unable to load nvidia module). I fix via apt-get update who suggested me to execute a command which finished the upgrade. X started again. Good. 

But right now the system starts and tell me that it does not know what versione of gnome is running. In fact there are some little problems, icons in the main menus aren't there anymore. 
Ok, apt-get update and upgrade tells me there are 19 packages to upgrade. 

launch the upgrade, download everything but four packages: 

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.5-10_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.5-10_all.deb)  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_20051028+1ubuntu7_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_20051028+1ubuntu7_all.deb)  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-10-386_2.6.17.5-10_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-10-386_2.6.17.5-10_i386.deb)  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-10_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-10_i386.deb)  404 Not Found

In fact they do not exists, the *-10 version does not exist, *-9 exist on repository and is the version I have installed right now. 

Why is he trying to get those packages?
More important, how do I tell him not to finish the upgrade of the other 15 packages already download that are needed to the system to work properly?

--fix-missing and -m options fails to give me any results. 

Thanks.

---

### Post by John.Michael.Kane on 2006-10-11
Those files do exist.

Remove the au from the front of the repo like shown.
[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-10_i386.deb)

now try to aptitude install them or let synaptic get them.

---

