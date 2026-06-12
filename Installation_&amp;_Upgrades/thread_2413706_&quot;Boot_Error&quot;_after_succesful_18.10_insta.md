---
title: "&quot;Boot Error&quot; after succesful 18.10 installation"
date: 2019-03-01
forum: Installation &amp; Upgrades
---

### Post by laureegrd on 2019-03-01
Hi, I am new to Linux and wanted to install Lubuntu on my low-spec laptop. I followed the guide at docs.lubuntu.net, and everything seems to work fine but when it finishes and I restart and boot from the desired HDD, nothing happens and it takes me back to the boot menu.

So I tried using the "boot from first hard disk" option on the iso (which I flashed on a USB drive, btw) but the only thing I get is "Boot error".

Checking the partitions from KDE inside Lubuntu Live shows the expected. I have set up a 40gb partition with mount point /, and the rest of the disk with mount point /home.
Also made sure to set the "Device for boot loader installation" on this same HDD when installing.

Also, my BIOS doesn't have a lot of options. UEFI is turned off and Legacy is enabled. Secure mode is not there at all, I don't know if that could be the problem. Fast boot is of course disabled.

Here's a boot-repair log: [http://paste.ubuntu.com/p/TRnZcSPjvw/](http://paste.ubuntu.com/p/TRnZcSPjvw/)

---

