---
title: "Need install advice for a raid0"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by mindead on 2010-04-19
I would like to know if I'm better to go with the 9.10 version or the 10.04 beta. 

The main reason I ask for this is that I have a 2 HD controlled by a Intel 57 series board (Intel Matrix Storage technology) in raid0 mode, which should be supported by linux under those requirements:

```

Beginning with Linux* kernel version 2.6.18*, the dmraid* utility 1.0.0-rc15 supports RAID 0, RAID 1, and RAID 10.

Beginning with Linux kernel version 2.6.27*, the mdadm* utility 3.0 supports RAID 0, RAID 1, RAID 10, and RAID 5.

```

Also, I have an i3 cpu (64 bits), meaning I'd like to have a 64bits os. I have made an attempt to install beta version 10.04, but it fails at partitionning the raid volume. I can see the raid volume in the disk manager, but it's deactivated. I've also tried with version 3.1.1 of mdadm, without success.

I would like to know if someone has already done it in a similar configuration.

Thanks a lot.

---

### Post by utnubuuser on 2010-04-19
I happened to be checking out Kubuntu-Beta download last night, and noticed that for raid configurations the alternate CD was required.  Might or might not apply in your case.

---

### Post by mindead on 2010-04-19
I read this and it seems to apply to my case: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). 

> The installer partitioner does not understand dmraid partitions properly 

I'll try it tonight.
Thanks!

---

