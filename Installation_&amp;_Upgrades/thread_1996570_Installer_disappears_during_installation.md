---
title: "Installer disappears during installation"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by rindi on 2012-06-04
Hi,

I've seen this happen on several, mainly older hardware and the newest LTS 12.04 Version of Ubuntu. It happens not only with Ubuntu, but other distro's that are based on that ubuntu version and use it's installer (like the newest rc version of mint, Linux Hybryde, etc).

I boot to the LiveCD or to a USB stick where I used unetbootin. Then when the OS is up and running, I start the installer. Everything works fine until I have entered all the necessary details (the user account I think is the last input needed). After that the "install" window just disappears from the display, but the mouse cursor still is turning, indicating something is running. But this goes on endlessly and the installation won't end.

If I run the installation on newer hardware I generally don't have any issues, and if I then move the HD I ran this installation on to the older hardware I had issues with, and start the system there, it runs fine, so it can't really be a hardware issue.

Is this a known bug and if so is there a solution or workaround for it, other than running the installation on other hardware?

Thanks for any help,
rindi

---

### Post by dino99 on 2012-06-04
try with boot option: nomodeset or noacpi

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by rindi on 2012-06-05
Thanks for the ideas, but those switches didn't help.

---

### Post by colin.p on 2012-06-08
I know how you feel, as I have an old athlon 1800+ (download server) running xubuntu 10.04X386. I can run the xubuntu 12.04X386 CD live, but when I try to install, it quits and throws me back to the live environment. I can, however, install that xubuntu 12.04 cd in VB on my ubuntu 12.04X64 laptop so I know it works ok.

I am in no hurry, so I will wait until 12.04.1 in August and hopefully it will install.

---

### Post by wilee-nilee on 2012-06-08
Try the alternative cd install.

---

