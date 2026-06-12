---
title: "Problem with installation Ubuntu from preseed"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by horizn on 2016-03-21
Hi,
I've prepared Ubuntu preseed file as mentioned:

[https://help.ubuntu.com/lts/installation-guide/example-preseed.txt](https://help.ubuntu.com/lts/installation-guide/example-preseed.txt)
with a help from:
[https://help.ubuntu.com/community/InstallCDCustomization/PreseedExamples](https://help.ubuntu.com/community/InstallCDCustomization/PreseedExamples)

I've configured Apache to serve preseed file, and checked is it available from network:
[http://ubuntu.domain.com/trusty/ubuntu-desktop.txt](http://ubuntu.domain.com/trusty/ubuntu-desktop.txt)

(I already have preseeds for Debian Squeeze, Wheezy and Jessie and all are working as expected)

Then booted PC from CD, and highlighted "Install Ubuntu" and pressed F6. I've changed file=/cdrom/preseed/ubuntu.seed to
url=http://ubuntu.domain.com/trusty/ubuntu-desktop.txt interface=eth0. Unfortunately installer go to standard questions about language, keyboard, partitioning scheme etc. instead use preseed file. I've checked apache logs and it not even asked for preseed file.

What went wrong?

---

### Post by horizn on 2016-03-21
With the Kickstart and Preseed manuals I could not bring up an unattended install of Ubuntu 14.04. Desktop 64-bit.  Is there somewhere a manual how to start installation from preseed file?

---

