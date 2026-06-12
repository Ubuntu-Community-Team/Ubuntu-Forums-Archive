---
title: "Is it possible to install ubuntu 12.04 on softraid throught livecd?"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by acidrop on 2012-11-23
Hello

I am trying to install ubuntu 12.04 desktop through livecd to a softraid (mdadm) raid0 disk.
What I have done is:

sudo apt-get install mdadm
created an /dev/md0 disk and and a ext4 partition where root (/) is installled.
Installation is completed successfully until the step which grub is installed.
On that step i get the following error:
Executing 'grub-install /dev/sda' failed.

This is a fatal error.
After that it gives me the option where to install grub and i choose /dev/sda.

The installation finishes successfully but when I reboot the machine ubuntu does not boot.
What am I doing wrong? I don't want to use alternate cd to do the installation...

---

### Post by acidrop on 2012-11-24
I've managed to get grub successfully installed by using boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

