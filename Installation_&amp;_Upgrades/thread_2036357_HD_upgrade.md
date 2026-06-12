---
title: "HD upgrade"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2012-08-01
Hello all,
classic question: I want to upgrade my system disk and I don't want to install. It'll be a bigger disk so I can't just simply use 'dd' on the devices.
Google returns plenty of hits, such as this [straightforward one]("http://www.infidigm.net/articles/ubuntu_hdd_upgrade/"), but Isn't there a difference between grub and grub2 ? Whic one does that tutorial use and how do I know which grub I have ?
Thanks

---

### Post by CharlesA on 2012-08-01
You can use dd and shouldn't have to mess with grub.

You could also use clonezilla or the like.

---

### Post by dargaud on 2012-08-02
I did just that: I booted into clonezilla and cloned the old drive onto the new one. It took only 3 minutes for 64Gb of SSD !

But then the new disk had partitions the exact same sizes. So I booted into a KUbuntu live CD, launched Kparted, disabled and deleted the swap partition, enlarged and moved the 2nd partition (which contained the swap) to the end of the free space, re-created the swap within, enlarged the main partition to the max, saved and then used "sudo swaplabel -U ... /dev/sda5" to assign the old UUID to the new swap partition. Took 5 another minutes and now my old server is back online with greatly extended powers...

---

