---
title: "Luks ssd"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by petersmith882 on 2010-08-17
Hello

I have installed an Intel X25-M SSD in my work laptop. I want to encrypt this SSD with LUKS and install Ubuntu 10.04 on it. LVM is not needed so this will not be configured.

The articles on SSD i have read, explains that it is very important to align the partitions correctly. Therefore i run fdisk like this:

fdisk -H 32 -S 32 /dev/sda

Then i have created three partitions boot, swap and root. Could i just go on and continue to configure LUKS like explained in this article:

[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

And then everything will be aligned as it should? or does dm-crypt need to be aligned somehow?

---

