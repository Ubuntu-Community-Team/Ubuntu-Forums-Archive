---
title: "I want to reinstall Windows on my Ubuntu computer"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by LorteMidget on 2012-08-24
Hi there. I would like to reinstall Windows on my Ubuntu 12.04 LTS computer, because my brother needs it for his school and he does not want to run Ubuntu on it.

It is a Lenovo Netbook, so there is no CD drive, but that is not my problem, since I made a bootable USB drive.

I tried booting the computer from the USB drive, the installation started (copying files only). But when it was done copying and needed to restart it just startet Ubuntu once again.

So is there any way to delete Ubuntu and install Windows on the computer without dual-booting, running Windows alongside Ubuntu?

---

### Post by darkod on 2012-08-24
Lets see if I understand this right: You want to completely overwrite ubuntu with windows?

In that case, when the partitioning step comes during the windows installation (when it asks you where to install), simply click on Advanced and delete all existing partitions. That will delete all partitions on the disk, deleting all data. So be careful unless you are OK losing the data.

After they are deleted, select the free space left (the whole disk will be free space without partitions), and create one partition. It can take the whole disk by default, or select a smaller size yourself if you want later to create a second partition from the remaining space.

Select this partition as destination for the install, continue the process and that should be it.

---

### Post by LorteMidget on 2012-08-24
You understood it right! I want to delete Ubuntu completely.

I'll try it, thanks :)

---

### Post by LorteMidget on 2012-08-24
The only option I get when I am going to choose whether to delete the whole partition or create a new is to install Windows on the C drive, which apparently is my USB drive, which makes no sense..

---

