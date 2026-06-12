---
title: "FAILED: AMD Catalyst(TM) Proprietary Driver-8.881"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2011-09-24
ThinkPad x120e
Ubuntu Desktop Natty 64-bit

I initially enabled the FGLRX AMD Proprietary Driver via the "Additional Drivers" menu. My video worsened, with dramatic if intermittent flickering being the result. I then decided to try to install the latest driver from the AMD site. Here's the output from my attempted installation:

[B]$ sudo sh ati-driver-installer-11-8-x86.x86_64.run --buildpkg Ubuntu/hardy
[sudo] password for mslundy: 
Created directory fglrx-install.6F6Chc
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.881......................................................................
eval: 1: ./ati-installer.sh: Permission denied
Removing temporary directory: fglrx-install.6F6Chc[/B]

I've no idea what might be wrong. Suggestions, please? Thanks.

---

