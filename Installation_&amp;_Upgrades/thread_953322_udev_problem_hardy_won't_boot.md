---
title: "udev problem? hardy won't boot"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by htedrom on 2008-10-20
hey all, 

i'll make this as brief as i can, if you need any more info, check this link to my problem on launchpad:
 [https://answers.launchpad.net/ubuntu/+question/48507](https://answers.launchpad.net/ubuntu/+question/48507)

basically, my new install of hardy won't boot because it can't mount any partitions on my first hard drive. I know this because I can't mount them from the livecd.. partitions on sda don't show up in /dev, but they DO show up in lshw and cfdisk.

i ran the command:
blockdev --rereadpt /dev/sda

and voila, sda1-4 showed up in /dev/, and could be mounted. i mounted the / partition and looked at the logs.. none of them have been changed since the upgrade, ie, the drive isn't getting mounted at boot.

what now?

thanks in advance

EDIT: here's the livecd dmesg on pastebin... you can see some errors around the lines 400-550: [http://pastebin.com/m57f8680b](http://pastebin.com/m57f8680b)

EDIT2: when i try booting hardy, it halts at around line 580. looks like my problem is on line 483-484:

#[   41.041915] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
#[   41.042083] ldm_validate_partition_table(): Disk read failed.

---

### Post by htedrom on 2008-10-20
think this was the problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222547)

---

