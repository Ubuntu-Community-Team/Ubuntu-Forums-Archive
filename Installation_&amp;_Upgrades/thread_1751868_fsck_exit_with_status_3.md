---
title: "fsck exit with status 3"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by gpost3 on 2011-05-07
Can't boot into Ubuntu. Using recovery mode, I get fsck exit with status 3 error. I did man on fsck and there is no reference to status 3. Same issue as [http://ubuntuforums.org/showthread.php?t=457612](http://ubuntuforums.org/showthread.php?t=457612) 

Please help as I have my data on sdb3 which is having this issue. File system is ext4. I can't go into shell or anything, I get the fsck error and the system reboots right away and stuck in that loop.

---

### Post by jramshu on 2011-05-07
```
The exit code returned by fsck is the sum of the following conditions:
1    - File system errors corrected
2    - System should be rebooted
```

So what it's telling you is it fixed a problem and the machine needs a reboot.
I see you said it rebooted on it's on. Are you saying it just keeps doing it?

---

### Post by gpost3 on 2011-05-07
that's exactly what it does. It keeps on checking the file system over and over again and keep rebooting every single time.

---

### Post by gpost3 on 2011-05-07
any ideas what is wrong with it? I also tried doing a file system check using gparted in live cd but it returned error saying the partition is already mounted when it actually isn't.

---

### Post by gpost3 on 2011-05-08
one thing I did do was run fsck on mounted partition. Any way to fix this?

---

### Post by Sidewinder1 on 2011-05-08
One thing I have heard/read, over the years is NOT to run fsck on a mounted drive! That may have been what caused the problem. I don't really have a fix but a good starting point might be to boot to LiveCD and go from there.

Side

---

