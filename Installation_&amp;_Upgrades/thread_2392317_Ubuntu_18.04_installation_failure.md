---
title: "Ubuntu 18.04 installation failure ??? ???"
date: 2018-05-19
forum: Installation &amp; Upgrades
---

### Post by kostasan on 2018-05-19
I try to install Ubuntu 18.04 64bit.
When I reach the screen where you choose if you want Third party software, updates during install,normal/minimal install and I press continue, I get the following error pop up message
```
??? ???
??? ???
```

The sha1 sum of the iso file I used to burn the cd is correct and the Live-CD works fine (execpt from the installation part...)
I also tried ```
sudo apt update
sudo apt upgrade
``` and ubiquity was updated to a newer version.

I have booted both as UEFI and Legacy.

Any clues?

---

### Post by oldfred on 2018-05-19
You may want to file a bug report. It should at least give some idea of issue.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)

It is often next scanning drives/partitions. Perhaps error in partitions causes crash?
Post this to see if partitions look correct:
sudo parted -l

---

