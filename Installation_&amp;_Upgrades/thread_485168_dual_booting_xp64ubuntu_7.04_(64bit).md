---
title: "dual booting xp64/ubuntu 7.04 (64bit)"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by dartkel on 2007-06-26
I was quite happy with Ubuntu but wanted to try XP64 on my second hard disc (IDE). Ubuntu is on my SDA disc.
Unfortunately now I have XP64 only and cannot get dual booting to operate. I have GAG but it does not recognise the Ubunto sda disk. On the XP system the boot loader is as below:

[boot loader]
timeout=6
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

My question is:
1. Can I modify the above to boot up Ubuntu?
or
2. Can I use some other loader and modify it. I can see no way of finding out how to modify GAG.

---

### Post by Vajra Vrtti on 2007-06-26
I think think can help you:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by dartkel on 2007-06-27
Many thanks, worked fine.

---

