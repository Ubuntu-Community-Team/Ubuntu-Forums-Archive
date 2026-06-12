---
title: "Cannot set-up a manual encrypted LVM setup when installing from USB"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by Faolan84 on 2012-11-04
I went to install Kubuntu 12.10 on my laptop so I could have the latest and greatest, but the installer seems to have one major oversight that will not let me install Quantal. This is a major oversight, and one of the reasons why in the past I always had to install from the "alternate installation" ISO which is no longer provided. It would be nice to see a late release of a working "alternate installer" or a 12.10.1 fix for this issue as it is a major show stopper since it would require me to back up and reload all my data to my laptop again which is something most do not have time to do.

Don't get me wrong, I am glad that the main installation program is getting some of the options of the Debian text installer, but it seems to have the same rough edges as it has in detecting complex disk setups and operations. As a long time Kubuntu user this is a bit of a disappointment as KDE has always been my favorite desktop environment and Kubuntu has the easiest setup of all the distros despite its few hangups.

So basically a run down of what happens:
I go into disk setup and click manual. For some reason the installer thinks that the USB stick should be /dev/sda which is to be expected, but instead of a listing of partitions on /dev/sdb it shows nothing. I go to click /dev/sdb and it asks me if I want to wipe the partition table. I have no other options.

What it should do:
It should be able to detect the existing partitions and LVMs on my device, so that I can select which volumes I want to format (/boot, /, swap) and which ones I want to just set mount points to (/home).

This is a very big oversight in a world where disc technology is being rapidly replaced by much faster and sturdier flash and where LVM encryption is becoming a standard preferred solution for securing data on Linux based desktops. It is a also something that Fedora, OpenSUSE, and Debian have supported with ease for years and so did K/Ubuntu through the text-mode installer until they decided to remove it prematurely.

Also, the Startup Disk Creator did not want to transfer the ISO data from the installer to the USB drive properly and I had to use the old "dd bs=4M if=kubuntu.iso of=/dev/sdc" trick to get it a bootable installation medium. It checks out properly, so I know this was not why.

On the bright side, I am running 12.04 LTS and it is supported for five years, but for the love of all that is sacred please fix this!

---

