---
title: "ubuntu 14.04 install via Kickstart is missing the initial user"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by i2dave on 2014-04-30
Hi

I'm upgrading an existing 12.04 kickstart installation to 14.04, and for the most part the ks.cfg file is the same (few packages amended).

However, the initial user, which is created and becomes the sudo user for local admin, isn't being setup!  My configuration sets up rsh access from a main server, which is used to do any post-processing that the kickstart process fails on, so I can add the missing user manually, but this wasn't necessary in 12.04!

My question is: has the kickstart process changed somewhat between 12.04 and 14.04, so that some features are no longer implemented, or have they altered significantly?  There's quite scant info on Kickstart for ubuntu, which is quite surprising given that it's a fairly major timesaver for multiple deployments.....

My ks.cfg file was originally generated in 12.04 using the system-config-kickstart interface, then copied to the deployment server for text-based installs over http.  Everything else - location, timezone, partitioning, nis, dhcp, packages and post-install setup of things like fstab, etc - works fine.  It's just the user that's not added to /etc/passwd or /etc/shadow :(

Any clues / ideas?  It's got me stumped....

Thanks

---

### Post by i2dave on 2014-05-13
If I use the useradd function in the %post section, will this default as the sudo user?  Still stumped as to why the normal user creation doesn't add it to the passwd file :(

---

