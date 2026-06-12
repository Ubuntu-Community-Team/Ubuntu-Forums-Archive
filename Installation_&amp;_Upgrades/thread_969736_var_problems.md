---
title: "/var/ problems"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by darkreaction on 2008-11-03
After the upgrade to 8.10 I keep getting kicked out of my GUI boot into a text boot. It first tells me its changing the ownership of a lot of "/var/" files and to read only. The problem is when I get to "/var/run/klogd/kmsgpipe.pd" It says "the file could not be opened" and then reboots.  I'm in recovery mode now and everything seems to be working fine, but I would like to boot into my regular install. Any help appreciated Thanks.

---

### Post by taurus on 2008-11-03
What is the permission of /var/run/klogd/kmsgpipe.pid?

```
ls -la /var/run/klogd/kmsgpipe.pid
```
This is what it looks like on my machine.

```

total 8
drwxr-xr-x  2 klog klog 100 2008-10-27 09:28 .
drwxr-xr-x 16 root root 640 2008-10-27 09:28 ..
-rw-r--r--  1 klog klog   5 2008-10-27 09:28 klogd.pid
prwx------  1 klog klog   0 2008-10-30 18:03 kmsg
-rw-r--r--  1 root root   5 2008-10-27 09:28 kmsgpipe.pid

```

---

### Post by darkreaction on 2008-11-04
I came up with ```
-rw-rw-rw- 1 root root 5 2008-11-01 18:15 /var/run/klogd/kmsgpipe.pid

```

---

### Post by taurus on 2008-11-04
Try changing the permissions for /var/run/klogd/kmsgpipe.pid.

```
sudo chmod 644 /var/run/klogd/kmsgpipe.pid
ls -la /var/run/klogd
```

---

### Post by darkreaction on 2008-11-04
Ok I got ```
total 16
drwxr-xr-x  2 klog klog 4096 2008-11-01 18:15 .
drwxr-xr-x 20 root root 4096 2008-11-04 13:50 ..
-rw-r--r--  1 klog klog    5 2008-11-01 18:15 klogd.pid
prwx------  1 klog klog    0 2008-11-03 14:32 kmsg
-rw-r--r--  1 root root    5 2008-11-01 18:15 kmsgpipe.pid
```

---

### Post by taurus on 2008-11-04
Reboot and see if you can log in now.

---

### Post by darkreaction on 2008-11-04
Nope no good. here is all I get ```
Cannot open socket /var/run/acpid.socket : address already in use
```
```
Chown /var/log/  "on like 20 files"
```
```
Cannot make /var/run/klogd/kmsg : file exists
```
```
Changing owners /var/run/klogd/kmsgpipe.pid : unable to open
```

then reboots.

---

### Post by Ruiner75 on 2008-11-05
Same problem here. See also:

[http://ubuntuforums.org/showthread.php?t=966356](http://ubuntuforums.org/showthread.php?t=966356)

[http://ubuntuforums.org/showthread.php?p=6097291](http://ubuntuforums.org/showthread.php?p=6097291)

---

