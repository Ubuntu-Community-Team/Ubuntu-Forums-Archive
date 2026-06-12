---
title: "Partition manager doesn't dectect hda"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by c_plus_plus on 2007-02-22
I have been helping a friend install Ubuntu on his laptop. We started by trying to install ubuntu by clicking on the install ubuntu Icon. We went through the installer, and we got stuck when we needed to choose the partition to install ubuntu on. The installer nor gpart recognized the main hdd. I probed around and discovered there was a hda file under /dev/, when I attempted fdisk /dev/hda the command returned a line saying:
    you will not be able to write the partition table.
nonetheless, I tried to add an ext3 partition only, to little surprise find that I couldn't write the partition table.

His primary hdd is on a sata bus on his laptop. Does anyone know how I can install ubuntu or somehow write a ext3 partition to his hdd?

---

### Post by c_plus_plus on 2007-02-23
bump

---

