---
title: "WUBI Install Failure. Logs Attached."
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by Ashish_Singhal on 2014-10-13
Hi,

I tried installing Ubuntu on my Windows 7 laptop with WUBI and encountered a permission error in the end. I have attached the end part of logs for reference.

Thanks
Ashish

---

### Post by Impavidus on 2014-10-13
Are you sure you want to install Ubuntu using wubi? See this sticky: [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

We may be able to help you installing Ubuntu as a normal dual boot.

---

### Post by hakuna_matata on 2014-10-14
> **Ashish_Singhal said:**
> 
I tried installing Ubuntu on my Windows 7 laptop with WUBI and encountered a permission error in the end. I have attached the end part of logs for reference.

From your log:
> ```
Traceback (most recent call last): 
  File "\10-13 08:14 ERROR  root: Could not remove: D:\ubuntu\install\ubuntu-14.04-desktop-amd64.isolib\wubi\backends\common\backend.py", line 426, in download_iso 
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
```
IMHO this error has occurred because of a previous error.

If you are using Ubuntu 14.04.1, maybe previous error is related to [bug 1367071]("https://bugs.launchpad.net/wubi/+bug/1367071")

---

### Post by Vladlenin5000 on 2014-10-14
Again, please read this: [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

