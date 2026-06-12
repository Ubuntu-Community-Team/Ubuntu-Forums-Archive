---
title: "Ubuntu 12.04.1 LTS Install on ideapad 310"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by M.D.G. on 2012-09-08
Let me preface this by saying I am fairly new to Ubuntu, I have done a fair amount of searching but nothing seems to answer my exact question.

I just got a IdeaPad 310 with 32GB of SSD + 500GB HDD. I would like to keep Windows 7 on the machine and also put a Ubuntu partition on. I've attempted to follow this tutorial

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

But Ubuntu does not seem to be recognizing the partition. I have tried booting in both AHCI and RAID as discussed here but this does not seem to do anything (other than cause problems when I try to boot into windows)

[http://ubuntuforums.org/archive/index.php/t-2020076.html](http://ubuntuforums.org/archive/index.php/t-2020076.html)

If I run Ubuntu from the USB and look at my partitions in GPart I see attachement 1 (I shrunk my windows partition through Windows)

When I get to the installation Type screen I can't seem any partitions, and if I try to click install I get attachement 2

Any help is much appreciated.

---

### Post by 2F4U on 2012-09-09
Looks to me as if you already have four primary partitions and with BIOS partitioning thats all you can have.

[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

---

