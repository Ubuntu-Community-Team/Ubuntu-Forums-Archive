---
title: "Installation issues just starting"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by xirrin on 2010-04-30
I had 8.04 and 9.04 installed previously. I have had Windows XP and Windows 7 installed on this drive. Yesterday I went to install 10.04 and the installation seemed to work fine until the reboot when I got a bad_sector error that ran across the screen and would then hang after the "Boot from CD:" prompt. I tried installing both x64 and x86 with the same result. From there, knowing that I had installed 8.04 fine previously tried to install that and would just upgrade it from there. After a few minutes into the install I got a "Installer Error" message and the computer would reboot to the Live CD.

I installed both XP (x86 and x64) and Windows 7 fine again today, but got the same errors again when I attempted to install Ubuntu.

Any ideas on what the problem might be? I have not changed any hardware since I had successfully installed and run 8.04.

---

### Post by cariboo on 2010-04-30
Have you tries booting the Live cd, then once at the desktop, open a terminal and run:

```
sudo fsck -y /dev/sdx
```

where /dev/sdx is your / partition.

---

### Post by xirrin on 2010-04-30
> **cariboo907 said:**
> Have you tries booting the Live cd, then once at the desktop, open a terminal and run:

```
sudo fsck -y /dev/sdx
```

where /dev/sdx is your / partition.

```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1: clean, 7856/17940480 files, 1238239/71746282 blocks
ubuntu@ubuntu:/$

```

---

### Post by xirrin on 2010-04-30
The error message is as follows:

```

[1664.372732] end_request: I/O error, dev sr1, sector 5108

```

This repeats across the entire screen with different beginning and ending numbers (always starting with 1664.3).

It finally stops and ends with this message and then hangs there:

```
init: plymouth-splash main process (22590) terminated with status 1
```


Any ideas?

---

