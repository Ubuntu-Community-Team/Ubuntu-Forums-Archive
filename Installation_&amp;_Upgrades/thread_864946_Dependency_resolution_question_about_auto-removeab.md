---
title: "Dependency resolution question about auto-removeables"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by kkjaergaard on 2008-07-20
I have package A, B and C. A depends on B and C, so when I install A, B and C also gets installed.

I then want package D which conflicts C. So when installing D, C and A (because A depends on C) gets removed.

Summary:
[LIST]
[*]A depends on B and C.
[*]I install A - B and C gets installed automatically.
[*]D conflicts C.
[*]I install D - C and A gets removed automatically.
[*]I now have only B and D installed.
[/LIST]

What happens to package B now? Is it marked as auto-removeable, and will it be automatically removed?

I was just wondering what apt-get, aptitude or Synaptic does in this case. I came to think about this then I proposed removing ubuntu-desktop in [an other thread about changing to KDE4]("http://ubuntuforums.org/showthread.php?t=864303").

---

### Post by bapoumba on 2008-07-20
apt-get has now an "autoremove" option:
>  autoremove
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.


```
sudo apt-get autoremove
```

aptitude does it too, but I would not recommend to use aptitude if you have been using apt-get/synaptic so far (they do not share their logs, so the outcome can be risky).

---

