---
title: "Wubi on D: partition doesn 't work!"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by PCman13 on 2010-06-13
Hi there!

I installed Ubuntu 10.04 with WUBI. In the setup wizard in windows, I selected the D partition to install Ubuntu on. It extracted the files, and after a reboot, and selecting Ubuntu, the Ubuntu setup wizzard appeared. After it was done, it rebooted. I selected Ubuntu, and this appeared on my screen:

```


booting from (hd0,0)...


```

And there it stucks!:mad: I tried editing C:\boot.ini, to let it select the ubuntu files. 

My original boot.ini file:

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

```

edited:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
D:\ubuntu\winboot\wubildr.mbr = "Ubuntu"

```

Then I get the following error:

```

Could not find <systemroot>\system32\HAL.dll

```

edited 2:

```

[boot loader]
 timeout=30
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
 D:\wubildr.mbr = "Ubuntu"

```
 (i copied the files insite D:\ubuntu\winboot)

Same error:
```

Could not find <systemroot>\system32\HAL.dll

```

Does anyone know how to solve this problem? I have very little space on my system partition (C:\) So, I installed it on D:\. I'm using Windows XP Professional SP2.

---

### Post by bcbc on 2010-06-13
I've done this before (installed wubi on a different drive - in fact it was an external drive) - so that works... without editing boot.ini

So probably something else has gone wrong. Not much to go on though - you said it went through the complete install.
Did you do anything out of the ordinary?

---

### Post by PCman13 on 2010-06-13
> **bcbc said:**
> I've done this before (installed wubi on a different drive - in fact it was an external drive) - so that works... without editing boot.ini

So probably something else has gone wrong. Not much to go on though - you said it went through the complete install.
Did you do anything out of the ordinary?
Nope. After the windows part of the installation was done, it said to reboot my PC. At that moment I was doing other things om my PC, so, i selected reboot later. When I rebooted, I selected Ubuntu and I came in the normal installation. That worked fine, and on the end, it rebooted my PC. From that moment it didn't work anymore.  

Ill try to fix it by removing WUBI via my control panel and installing it again.

---

### Post by bcbc on 2010-06-13
> **PCman13 said:**
> Nope. After the windows part of the installation was done, it said to reboot my PC. At that moment I was doing other things om my PC, so, i selected reboot later. When I rebooted, I selected Ubuntu and I came in the normal installation. That worked fine, and on the end, it rebooted my PC. From that moment it didn't work anymore.  

Ill try to fix it by removing WUBI via my control panel and installing it again.

EDIT: just re-read... I don't think it matters if you 'restart later'. That seems a bit strange, particularly as you did get to install the OS. I was referring to rebooting inbetween, which I realise you didn't do. So 'm at a bit of a loss to explain this

But after you've done the uninstall/reinstall - we'll know more.

---

### Post by darkod on 2010-06-13
I don't have much experience with wubi but I think wubildr.mbr stays on C: regardless which partition you use for wubi. You don't need to change the path to D:.

Having said that, it should have worked right away properly as it seems. This is why I don't like wubi and don't recommend it. You have very little to troubleshoot even. Everything is inside a root.disk image file.

It's very different with installation on separate partition as proper dual boot.

---

