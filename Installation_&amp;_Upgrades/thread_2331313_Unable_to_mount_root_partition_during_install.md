---
title: "Unable to mount root partition during install"
date: 2016-07-20
forum: Installation &amp; Upgrades
---

### Post by hiramabif2 on 2016-07-20
I'm currently a doing a "dry run" install of Ubuntu in VirtualBox to test it out before I install it on my main computer.

Here is my partition setup. This mirrors the setup I have on my current Debian PC:

Setup: [https://i.imgur.com/n9rok0I.png](https://i.imgur.com/n9rok0I.png)

For those who don't want to look at the picture, it's:

/dev/sda1 - 500MB ext4 /boot
/dev/sda5 - Encrypted ext4 /

/dev/sdb1 - Encrypted ext4 /home

Boot loader on sda1.

Here is the problem I get: [https://i.imgur.com/zJwLCFy.png](https://i.imgur.com/zJwLCFy.png)

Anyone have an idea as to why this is happening? Thanks!

---

