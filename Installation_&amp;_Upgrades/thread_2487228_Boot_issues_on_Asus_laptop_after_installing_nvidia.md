---
title: "Boot issues on Asus laptop after installing nvidia driver"
date: 2023-05-27
forum: Installation &amp; Upgrades
---

### Post by jocstaa on 2023-05-27
Hello, I am very new to linux. I just installed Ubuntu newly on my Asus rog strix scar 16 and everything seemed to work fine until after i installed the nvidia gpu driver using `sudo apt install nvidia-drivers-525`. After the reboot i keep running into boot up problems, sometimes it would boot up and sometimes it freezes on the boot up screen. Here is my boot-repair pastebin link: [https://paste.ubuntu.com/p/Stt8Cqr72H/](https://paste.ubuntu.com/p/Stt8Cqr72H/)

---

### Post by oldfred on 2023-05-27
Is -525 the correct driver for you card.
If not you have to totally purge it and install correct driver.

This says 530 is newer. But 525 was available.
[https://www.nvidia.com/en-us/geforce/drivers/](https://www.nvidia.com/en-us/geforce/drivers/)

Purge & reinstall
If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers autoinstall

---

### Post by jocstaa on 2023-05-28
On the nvidia driver website. I recommends -525 for my gpu: [https://www.nvidia.com/download/driverResults.aspx/204837/en-us/](https://www.nvidia.com/download/driverResults.aspx/204837/en-us/)

I use an RTX 4090(Laptop) gpu.

Also I did try purging and reinstalling but still no luck. The thing is it does boot up sometimes but it is very inconsistent, also usually when i boot up windows and then try to switch back to linux the boot freeze most definitely happens. Without the driver installed it works just fine

---

### Post by oldfred on 2023-05-28
Did you only install from Ubuntu repository, not directly from nVidia?

---

### Post by jocstaa on 2023-05-28
i have been installing the driver using `sudo apt install nvidia-drivers-525`. I havent tried installing from nvidia directly. I will try installing directly from nvidia and post my updates

---

### Post by jocstaa on 2023-05-28
Update: same effect using direct install from nvidia

---

### Post by oldfred on 2023-05-28
We do not suggest direct install from nVidia, just use nVidia site to confirm correct version is installed.
And I think the purge command does not work, you have to use nVidia tools to uninstall its driver.

Ubuntu makes some changes so with every kernel update the driver is correctly included. If the nVidia version, you have to manually do that with every kernel or other driver update.

---

### Post by ajohnl on 2023-05-29
Might be relevant to the OP. The first time I installed (22.04) I did what is often mentioned in reports on installing it. Clicked on drivers which is a section of update and it showed me 2 video card drivers. One tested and one straight nvidia so installed testing.

;) As oldfred knows i installed again. Somewhat different. No drivers offered. This turned out to be down to wifi hiccups during install so it missed the post release updates. Once that was fixed it selected the correct driver for me so I installed it.

Bit of a moral really. Use the desktop install when you can or make sure stuff comes from the release's repo's or you may get apt get bigcrash and other problems.

My recollection of direct nvidia driver from them installs is that they added an uninstall option as well but a number of years since I installed one. Picking which one can be tricky but they usually get it right.

---

