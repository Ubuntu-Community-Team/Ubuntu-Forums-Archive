---
title: "New installation of 12.04 fails to boot - Raid 1 degraded - Partiton 'inactive'"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by bigpoint2 on 2012-05-20
Hello,

wanted to do a new installation of 12.04 over a 10.04 system (on an Intel i5, 4GB system) and just keep the 'home' partition which has been on a software raid1.

Installed with alternate CD, everything fine, 'old' raid was detected during install and i made it 'home' while telling the installer to keep data.

After the installation the system now fails to boot due to  a degraded Raid. It says that one of the devices is 'inactive'. When I force to boot with the degraded array everything is fine afterwards. The Raid is up and working with the two disks/partitions, status is 'clean', all data is there. But after next reboot the eror is there again.

Even tried a 'clean' installation with a newly setup raid array during installation with newly formatted partitions - the same happens.

Can it really be, that Ubuntu boots 'too fast' for my devices to come up?
Never had a problem before under 10.04 - are there changes to the way Raid works or the devices are mounted/assembled during boot?

Do not want to live with that initially degraded raid-boot, am afraid of data loss. Any ideas?

Thanks,
Gerd

---

### Post by BAUSTIECH2 on 2012-06-11
DANGER - DO NOT USE UBUNTU 12.04 IF YOU HAVE ANY SOFTWARE RAID

There is a race condition that randomly marks good RAID arrays as failed.  This triggers an error that, due to another bug, ignores the "bootdegraded=true" kernel work-around parameter.  The end result is you end up in an initramfs shell called "busybox" that is a blackhole of doom and downage.

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220?comments=all](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/872220?comments=all)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/778520](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/778520)

And it's made much worse if you have nVidia video, which, due to another bug and/or driver issue, hides everything so you can't see anything of what's going on.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

---

