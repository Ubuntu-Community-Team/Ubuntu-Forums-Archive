---
title: "Ubuntu 23.04 -&gt; 24.04 Update Failure"
date: 2024-09-21
forum: Installation &amp; Upgrades
---

### Post by phlp on 2024-09-21
Have an issue upgrading my Ubuntu 23.04 to 24.04.1. From what I'm seeing, Ubuntu Pro is a requirement for upgrading to 24.04.1 but I haven't seen that called out anywhere.

Is it required or am I missing something? 

see output below

Thanks

P.S. Tried Software Updater and it exits with no message.


$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libheif1 libjs-jquery-ui libpathplan4 graphviz libgvpr2 libgvc6 libopenexr25
  python3-scipy libcgraph6 libmagickcore-6.q16-6-extra libcdt5
  libmagickwand-6.q16-6 imagemagick-6.q16 libmagickcore-6.q16-6 liblab-gamut1
  imagemagick-6-common libde265-0 libpmix2
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages have been kept back:
  dotnet-hostfxr-7.0 ubuntu-advantage-tools ubuntu-pro-client ubuntu-pro-client-l10n
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
phil@tower:~$ do-release-upgrade 
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

---

### Post by deadflowr on 2024-09-21
There is no direct upgrade path from 23.04 to 24.04.
23.04 is also end of life, so you'd need to change source configuration to the old release archives first, then you'd only be able to upgrade to 23.10.
Then you'd have to switch the sources back to the normal, non-old-release archives, and then you can upgrade to 24.04.
See:[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But seeing Pro mentioned i wonder if you're really running 23.04.
Pro works with LTS releases, I don't think it works with the standard releases like 23.04.

What do the outputs for
```
lsb_release -a
sudo apt update
```
show

And Pro is not a requirement to upgrade.
So that in itself not an issue here.

---

