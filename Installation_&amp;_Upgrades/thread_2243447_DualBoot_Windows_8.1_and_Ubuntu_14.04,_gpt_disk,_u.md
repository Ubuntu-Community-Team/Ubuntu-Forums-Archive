---
title: "DualBoot Windows 8.1 and Ubuntu 14.04, gpt disk, uefi, os not found?"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by ramo2 on 2014-09-08
[http://askubuntu.com/questions/521689/dualboot-windows-8-1-and-ubuntu-14-04-gpt-disk-uefi-os-not-found](http://askubuntu.com/questions/521689/dualboot-windows-8-1-and-ubuntu-14-04-gpt-disk-uefi-os-not-found)

Thanks in advance, it's been a long day.

I figured out the problem, Please delete this thread and its counterparts that were put in Jail.

---

### Post by fantab on 2014-09-09
Looks like a file system error. Run [Chkdsk]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html") on Windows C: partition which you 'shrank'.

Then booting your Ubuntu DVD/USB, "try Ubuntu'. Open Terminal [ctrl+alt+t], run the following commands and post the output here:
```
sudo parted -l
```

---

