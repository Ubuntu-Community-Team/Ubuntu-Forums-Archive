---
title: "Ubuntu 20.04 hwe installed by unattended upgrades"
date: 2021-02-11
forum: Installation &amp; Upgrades
---

### Post by corradoventu on 2021-02-11
On my Ubuntu 20.04 installed from 1st ISO 
```
mao@mao-x3-focal:~$ cat /var/log/installer/media-info
Ubuntu 20.04 LTS "Focal Fossa" - Release amd64 (20200423)
```
the hwe has been installed by unattended upgrades long time before Ubuntu 20.04.2
```
2021-01-11 16:41:17,807 INFO Starting unattended upgrades script
2021-01-11 16:41:17,808 INFO Allowed origins are: o=Ubuntu,a=focal, o=Ubuntu,a=focal-security, o=UbuntuESMApps,a=focal-apps-security, o=UbuntuESM,a=focal-infra-security
2021-01-11 16:41:17,808 INFO Initial blacklist: 
2021-01-11 16:41:17,808 INFO Initial whitelist (not strict): 
2021-01-11 16:42:26,576 INFO Packages that will be upgraded: firefox firefox-locale-en firefox-locale-it libopenexr24 libopenjp2-7 libp11-kit0 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libproxy1v5 libwavpack1 linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04 linux-libc-dev p11-kit p11-kit-modules python-apt-common python3-apt tzdata
2021-01-11 16:42:26,576 INFO Writing dpkg log to /var/log/unattended-upgrades/unattended-upgrades-dpkg.log
```

---

### Post by deadflowr on 2021-02-11
There have been some discussions on this and it turns out 20.04 now sets the hwe as the default on the desktop.
It's actually mentioned in the release notes, [https://wiki.ubuntu.com/FocalFossa/ReleaseNotes#Ubuntu_Desktop]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes#Ubuntu_Desktop")
So the hwe wasn't newly installed, but the system came that way.

---

### Post by grahammechanical on 2021-02-11
> This is the second point release in the [Ubuntu 20.04 LTS]("https://www.omgubuntu.co.uk/2019/10/ubuntu-20-04-release-features") series. It rolls together all of the software updates, security patches, and bug fixes issued to the *Focal Fossa* to date. Plus, it intros a **new hardware enablement stack** (HWE) composed of a new kernel and updated Linux graphics drivers.

[https://www.omgubuntu.co.uk/2021/02/ubuntu-20-04-2-lts-released](https://www.omgubuntu.co.uk/2021/02/ubuntu-20-04-2-lts-released)

Up until now My 20.04 has been using the 18.04 Hardware Enablement stack. I also found this interesting.

> Ubuntu [now tracks HWE by default]("https://discourse.ubuntu.com/t/improvements-for-hardware-support-in-ubuntu-desktop-installation-media/20606") on support hardware. This means regardless of when you installed Ubuntu 20.04 LTS (or what disc image you used) you get **new kernel releases every six months until 2022** (which is when the fifth and final point release in the series is made).

And this

> As Ubuntu chooses the best kernel for your hardware during install, only  hardware compatible with the HWE will opt you in to. Some systems may  (for hardware reasons) remain on Linux kernel 5.4. You can force install  the HWE kernel, but you may experience issues as a result.

My present install of 20.04 is using kernel 5.4. I also have 20.10 and 21.04 (development) installed and they have Kernel 5.8. So, I expect this 20.04 to get the newer kernel.

Regards

---

