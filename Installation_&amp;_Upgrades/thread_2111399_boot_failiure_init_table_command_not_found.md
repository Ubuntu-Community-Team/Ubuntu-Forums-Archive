---
title: "boot failiure: init table command not found?"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by richard4052 on 2013-02-01
Hi I installed Ubuntu 12.10 x64 on my Devil Tech Fragbook (OEM MSI GT70) but when it starts up i get the error below. I have searched google for ideas of how to fix but without any luck. I can run the OS live and use the OS without any problems, attempted reinstall still the same error upon boot.

[18.492972] [drm] nouveau 0000:01:00.0: 0x9904: init table command not found: 0xA9

Can any help would be much appreciated :)

Many Thanks

---

### Post by richard4052 on 2013-02-02
bump

---

### Post by rugebiker on 2013-02-04
i have this same issue trying to install fedora =/
any ideas?

---

### Post by userdrew on 2013-06-04
Hi.  I am also having this issue, but with Debian.  I think it has something to do with the nvidia drivers.
The system hangs during boot with the above line.

---

### Post by rugebiker on 2013-06-04
> **userdrew said:**
> Hi.  I am also having this issue, but with Debian.  I think it has something to do with the nvidia drivers.The system hangs during boot with the above line.Hey there, I found the issue for me. What happened is that my laptop has the new NVIDIA technology called NVIDIA Optimus,., and this has some issues on linux because NVIDIA hasnt released drivers for it. So if you also have NVIDIA Optimus, you need to look for something called the bumblebee project and install it under ubuntu to make the NVIDIA drivers work. I installed fedora and made it work there. I really don't know how to install bumblebee on ubuntu, but looking quick in google gives many results that may help.Good luck!

---

