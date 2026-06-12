---
title: "mount error"
date: 2016-04-02
forum: Installation &amp; Upgrades
---

### Post by thomas92 on 2016-04-02
Hello, when I install ubuntu on Nexus 7 via TWRP recovery, I get this error:
```

mount: mounting /dev/mmcblk0p9 on /root failed: No such device

Could not mount the partition /dev/mmcblk0p9.
This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removeable device without first unmounting or ejecting it. (filesystem = f2fs, error code = 255)

BusyBox v1.20.2 (Ubunti 1:1.20.0-8ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```
Previously the installation went without any problem. But suddenly I start to receive this error. I tried more times to install it but with no success. Any ideas?

---

### Post by SeijiSensei on 2016-04-02
/root is the home directory for the root user.  Why would you be mounting a filesystem there?

---

### Post by thomas92 on 2016-04-02
I don't mount anything. I install .img file in multirom and when I try to boot secondary ROM, I receive this error.

---

