---
title: "Boot fails after boot-repair"
date: 2016-09-29
forum: Installation &amp; Upgrades
---

### Post by christov2 on 2016-09-29
Hello,
after updating my notebook, the installation of grub stalled.

Then I issued the command
  [FONT=courier new]sudo grub-repair[/FONT]
 in a started xterm.

The notebook did not boot with the following message:

[FONT=courier new]    Mount failed for selinuxfs on /sys/fs/selinux: No such file or directory
[/FONT]

The saved diagnostics from boot-repair is here:

Meanwhile, I could solve the problem. The issue was an interrupted system update.
In my case the solution was:

1. I could boot an older kernel
2. sudo dpk --configure -a

Afterwards, I could boot the system as usual.

---

