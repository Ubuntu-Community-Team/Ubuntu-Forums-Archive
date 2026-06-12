---
title: "How to upgrade ZFS to v0.7 using 16.04?"
date: 2018-10-07
forum: Installation &amp; Upgrades
---

### Post by kebabbert on 2018-10-07
I am using Ubuntu 16.04.5 and want to upgrade the ZFS version to 0.7 or higher. Is there any recommended way to do that? I have read this thread, but some people are cautious as this ppa is not official. 
[https://www.reddit.com/r/zfs/comments/7e36o0/ubuntu_1604_zfs_073_anyone_got_it_running/](https://www.reddit.com/r/zfs/comments/7e36o0/ubuntu_1604_zfs_073_anyone_got_it_running/)

The problem is that ZFS in 16.04 is a bit flaky. I mount ZFS disks between Solaris and Linux, and the disk reports strange problems when Linux has mounted it. ZFS 0.6x is not stable.
Another problem is that my Supermicro and Xeon E3-1245 cpu does not like Ubuntu 18.04.1 because everything lags a lot. So I can not upgrade to 18.04.1 which means I am stuck at 16.04.

---

### Post by kebabbert on 2018-10-08
Ok, I installed ZFS 0.7.11 in Ubuntu 16.04.5 and it seems to work fine. I just followed the instructions in the thread above:
sudo add-apt-repository ppa:jonathonf/zfs
sudo apt-get update
apt install linux-headers-$(uname -r)
sudo apt install linux-headers-$(uname -r)
sudo apt install zfs-dkms

---

