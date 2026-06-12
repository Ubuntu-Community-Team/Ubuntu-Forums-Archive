---
title: "Getting rid of low disk space message"
date: 2014-12-20
forum: Installation &amp; Upgrades
---

### Post by sameer7 on 2014-12-20
Hi,
I am getting a low disk space message 
df command shows the following 

Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda10       6732784  6190344    177384  98% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1993732        4   1993728   1% /dev
tmpfs             400968      992    399976   1% /run
none                5120        4      5116   1% /run/lock
none             2004836      768   2004068   1% /run/shm
none              102400       80    102320   1% /run/user
/dev/sda8        6454632    14724   6088984   1% /media/sameer/d17ac334-0f4d-41ad-82a6-965f0f661d39
/dev/sda2       96093180 55769556  40323624  59% /media/sameer/6468BC1768BBE648

how can I increase the size of /dev/sda10
I am new to Ubuntu will appreciate if someone helps me get over it.
Thank you

---

### Post by deadflowr on 2014-12-20
> [COLOR=#000000]how can I increase the size of /dev/sda10[/COLOR]

It depends on what the sizes and contents are of sda1 through sda9 are.
run this command to helps us see how the disk is setup, partition-wise.
```
sudo parted -l
```
(Please use code tags when posting command outputs, see [here]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"))

Also post what system you have installed, so we can best determine the next course of action, without undue stress.

---

