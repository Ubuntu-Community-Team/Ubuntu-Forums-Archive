---
title: "Unable to get trackpad working in Chrubuntu on Acer C720!"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by 6tr6tr on 2014-11-10
I followed all the install guides for installing Ubuntu (it installed 14.04) and the way to get the trackpad working, but none of them have worked! What is the issue?

I followed all of these:

[http://ubuntuforums.org/showthread.php?t=2223738](http://ubuntuforums.org/showthread.php?t=2223738)
[https://97e83d70d72c338a5120d68abf78ce7c7e07d6e7.googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh](https://97e83d70d72c338a5120d68abf78ce7c7e07d6e7.googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh)

Also tried this: [http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/cflm7wo](http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/cflm7wo) did not work.
This also did not work: [https://gist.githubusercontent.com/anonymous/fd07a6ed49657b9248c8/raw/41d47935ca7f757bd7f01b62134ff3b79f9dce80/c720-3.16-patch](https://gist.githubusercontent.com/anonymous/fd07a6ed49657b9248c8/raw/41d47935ca7f757bd7f01b62134ff3b79f9dce80/c720-3.16-patch)

but nothing seems to work! What can I do to get it to work?

---

### Post by 6tr6tr on 2014-11-10
I'm getting the errors:

mv: cannot stat '/lib/modules/3.16.0-24-generic/kernel/drivers/i2c/busses/i2c-designware-core.ko': No such file or directory
mv: cannot stat '/lib/modules/3.16.0-24-generic/kernel/drivers/i2c/busses/i2c-designware-pci.ko': No such file or directory
mv: cannot stat '/lib/modules/3.16.0-24-generic/kernel/drivers/i2c/busses/i2c-designware-platform.ko': No such file or directory
cp: cannot stat 'drivers/i2c/busses/i2c-designware-*.ko': No such file or directory

---

