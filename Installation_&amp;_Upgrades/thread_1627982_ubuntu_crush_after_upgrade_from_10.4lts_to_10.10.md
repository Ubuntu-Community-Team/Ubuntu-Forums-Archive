---
title: "ubuntu crush after upgrade from 10.4lts to 10.10"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by pontdecheruy on 2010-11-22
Hi everyone,
I'm running Ubuntu 10.4Lts, within windows since 2 months now. I'm quite happy with it.
I did installed from CD but within Windows7 and allowed 30GB of space for ubuntu on my C drive.
I would like to upgrade to Ubuntu 10.10 but when i do so, my system wont boot anymore, i does all necessary installs but when comes to reboot after upgrade, ubuntu 10.10 won't boot at all. 
Can anyone help me with this issue???
Thanks in advance

---

### Post by mikewhatever on 2010-11-22
From the 10.10 release notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)
> You cannot upgrade if wubi is installed to a partition other than Windows. (610898,653134) 

Anyway, running Ubuntu from inside Windows is ok for evaluation purposes, but it's probably not a good idea to do so for months. If you plan on keep using it, do a proper installation.

---

### Post by pontdecheruy on 2010-11-22
thanks a lot, i just knew that it was because of wubi installation.

---

### Post by bcbc on 2010-11-22
You can get it booting by copying the c:\ubuntu\winboot\wubildr file over c:\wubildr.

Consider migrating your current wubi to partition if you want to keep your settings/data: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

