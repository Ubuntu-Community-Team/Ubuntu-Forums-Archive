---
title: "How to install repo script to download Android source code"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by quangtuan.bs on 2011-09-17
I'm a newbie with Ubuntu and Android, I want to download Android source code to study. But when I install repo script as [http://source.android.com/source/downloading.html](http://source.android.com/source/downloading.html), I receive this result:

```

newbie@ubuntu:~$ curl https://android.git.kernel.org/repo > ~/bin/repo
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
curl: (51) SSL peer certificate or SSH remote key was not OK
newbie@ubuntu:~$

```

How to fix this issue?

---

### Post by 2F4U on 2011-09-17
This may explain it a bit:

[http://code.google.com/p/android/issues/detail?id=19943](http://code.google.com/p/android/issues/detail?id=19943)

It seems to be an issue following the hack of kernel.org. This article suggests a workaround:

[http://php.webtutor.pl/en/2011/09/05/kernel-org-hacked-how-to-get-android-repo/](http://php.webtutor.pl/en/2011/09/05/kernel-org-hacked-how-to-get-android-repo/)

---

