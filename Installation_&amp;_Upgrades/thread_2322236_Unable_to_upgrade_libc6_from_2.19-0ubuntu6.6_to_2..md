---
title: "Unable to upgrade libc6 from 2.19-0ubuntu6.6 to 2.19-0ubuntu6.7"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by Amol_Patil on 2016-04-27
Hi,
- I tried to apply security upgrades to my Ubuntu 14.04.2 LTS box, but failed to upgrade libc6.
- For upgrade I used apt (apt-get update, apt-get upgrade)
- So I tried to download the debian package and install it using dpkg. This time it partially worked i.e. package got installed but with configuration failure. (in /var/log/dpkg.log I see: status half-configured libc6:amd64 2.19-0ubuntu6.7)

Has anyone faced this issue? How to fix it? My end goal is make security upgrade work flawlessly with unattended-upgrades.

Thanks,
..... Amol

---

### Post by wavemaking on 2016-11-27
Amol_Patil,

Did you find a solution to this? I have the same issue. The system sinmply freezes when it gets to configuring libc6.

---

### Post by Amol_Patil on 2016-12-14
I have not got any solution yet.

Thanks,
..... Amol

---

