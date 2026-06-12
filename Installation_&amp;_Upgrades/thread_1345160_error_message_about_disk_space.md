---
title: "error message about disk space"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by tamedcynic on 2009-12-03
So, I really am a beginner and I think I partitioned the hard drive wrong, because I am getting a message that reads:

Not enough free disk space
The upgrade needs a total of 378M free space on disk '/'. Please free at least an additional 135M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

What am I doing wrong here?

---

### Post by raymondh on 2009-12-03
> **tamedcynic said:**
> So, I really am a beginner and I think I partitioned the hard drive wrong, because I am getting a message that reads:

Not enough free disk space
The upgrade needs a total of 378M free space on disk '/'. Please free at least an additional 135M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

What am I doing wrong here?

DRS305 wrote a good tutorial about recovering disk space.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

If you want to know allocations and usage within the system files, access a terminal and type

```
df -h
```

If you want to resize and need assistance, post back with a screenshot of gparted (system > admin > partition editor).  You can take a screenshot by pressing PRTSCRN key or accessing the 'camera' (Applications > accessories > take a screenshot).  Save to desktop and attach to your next post.  It'll help the forum visualize your HD.

If you have difficulties with a screenshot, kindly post back results (from terminal) of

```
sudo fdisk -l
```


Regards,

---

