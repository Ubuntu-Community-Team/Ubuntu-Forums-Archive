---
title: "dmraid error"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by xwilx on 2007-06-14
Hi there, 

I have a new system with Intel-DG965OT mobo, Core2 Duo E6600 CPU, and 2G RAM. Two harddics setting up with the onboard raid 1. Running Windows XP on a partition.

Following this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
I am able to get Ubuntu Fiesty 7.04 up and running dmraid. Apparently dmraid is working OK, as I can see the two partitions in raid 1 mapped under /dev/mapper/isw_xxxxxxxxxxx.

Then at this point, I don't know if my setup is working fine. I don't see any real problem so far, but when I run "dmraid -ay", this is what I got:
RAID set "isw_cdbijcbdih_DEWENWIL" already active
ERROR: opening "/dev/.static/dev/mapper/isw_cdbijcbdih_DEWENWIL"

I don't know what this error mean. Under /dev/.static/dev, there is only a file 'fuse'. I worry a little about this error, can someone tell me what this error mean? And how I am going to fix it?

There is awfully too few documentations about dmraid on the web. Is there any way I can tell if my setup with dmraid is correct?

Any help would be appreciated.

Thanks a lot.

wil.

---

