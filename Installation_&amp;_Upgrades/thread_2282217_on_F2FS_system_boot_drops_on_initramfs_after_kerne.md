---
title: "on F2FS system boot drops on initramfs after kernel upgrade"
date: 2015-06-12
forum: Installation &amp; Upgrades
---

### Post by alexan on 2015-06-12
I did managed to install and run Lubuntu 15.04 x64
Everything went smooth with the default kernel (3.19.0-15-generic).
But whenever I try to use the latest stable kernel available... the system fail to boot into lubuntu and drops me on initramfs
These are the fstab only entries
```
UUID=2ff7fa1a-ad0d-451f-b69b-a92dbeeddc40     /            f2fs          rw,relatime,background_gc=on,user_xattr,acl,active_logs=6    0 0
UUID=0e97332c-69b0-4b84-bed7-d0c13b71a417 /boot           ext4    defaults        0       2
```

this is my /etc/initramfs-tools/modules
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
f2fs

```

and here: [http://pastebin.com/XgXq8myR](http://pastebin.com/XgXq8myR) the verbose result of my **sudo update-initramfs -uv**

the current available kernel on my system are:
3.19.0-15-generic (came with Lubuntu installation: system work)
3.19.0-20-generic (kernel update: system refuses to boot)
4.0.0-040000-generic (another update I tried after 3.19.0-20 wishful thinking to solve the issue: system still refuses to boot)

---

### Post by alexan on 2015-06-12
Nevermind...
**sudo apt-get install f2fs-tools --reinstall**
solved the issue

---

### Post by f4tmike on 2015-08-20
Similar problem here. I end up in a busybox. How could you make an **sudo apt-get install f2fs-tools --reinstall**?
The difference: it's the first installation and I've got Kernel 3.16.

---

