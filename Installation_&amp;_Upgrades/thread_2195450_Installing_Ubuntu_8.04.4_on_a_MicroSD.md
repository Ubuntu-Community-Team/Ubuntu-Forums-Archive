---
title: "Installing Ubuntu 8.04.4 on a MicroSD"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by h.hittini on 2013-12-24
Hello everyone,
I have a pretty good experience in windows but still new to Linux
I need to install Ubuntu/Debian on RB-110 [http://www.roboard.com/RB-110.htm](http://www.roboard.com/RB-110.htm)
The processor has an old architecture and I only have 256 MB of RAM so I decided to go with Ubuntu 8.04.4 LTS
I created a USB stick to install Ubuntu on a MicroSD connected to the built in card reader but here is my problem
After starting the Live CD I found that the installer doesn't see the MicroSD despite that the board sees it
The MicroSD appears on the boot menu and that's why I assume the car reader doesn't need a driver
I also tried Debian Squeeze and faced the same problem
However, Debian identified the LAN interface and got an IP from the DHCP server but Ubuntu didn't identify the interface at all
In addition, I wonder If you can help me in Installing a minimal version (without all the games, graphics and office applications) because I found that it doesn't have a graphical installer
Thanks in advance

---

### Post by claracc on 2013-12-24
I don't know about the micro card reading problem, but I do not advice to install ubuntu 8.04 in your pc since it is a not supported release and very old (2008). I think you cannot run a supported ubuntu release in a computer with such a low RAM.

I instead suggest you to try lubuntu (13.10 I think is the last), particularly with 256 MB RAM, I think the minimal install or perhaps the alternate iso can give you a working desktop (you have very little RAM). 

Please, see the following links to know more about lubuntu, minimal installation and hardware requirements:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)
[http://askubuntu.com/questions/162626/what-are-the-minimum-system-requirements-for-lubuntu](http://askubuntu.com/questions/162626/what-are-the-minimum-system-requirements-for-lubuntu)

---

### Post by h.hittini on 2013-12-24
"This kernel requires an i586 CPU, but only detected an i486 CPU.
Unable to boot - please use a kernel appropriate to your CPU"
That's what I get when trying to install a recent version of Ubuntu and what I got when tried to install Lubuntu 13.10

---

### Post by claracc on 2013-12-24
As I see in the hardware specifications of your pc it is compatible with Linux distribution kernel 2.4.x, 2.6.x, so you will have to look for a linux distro using kernel 2.6.x. 

There is not any ubuntu flavour supported release which use such kernel (as far as I know). I think you will have to look for other distros: puppy linux, sliztaz, bodhi linux

---

### Post by h.hittini on 2013-12-24
Ubuntu 8.04.4 LTS actually uses 2.6.24-26-generic kernel

---

### Post by claracc on 2013-12-24
Yes, but you have to be aware that ubuntu 8.04 reached its end of life years ago, for this reason won't receive any security updates, and the repositories with the software won't be in the server but you can find them here: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

It is a security risk to connect to internet with an EOL support release, apart of running old software which can be no compatible with some web pages.

---

### Post by Bucky Ball on 2013-12-24
Don't go there. This release has not been supported for two and a half years. Vulnerable and if you are online I suggest you get off-line if you actually manage to get this installed. As no one has used this for ages, you are unlikely to get much help with it.

Look for an alternative. Some have already been suggested (Puppy, Porteus or Peppermint might be worth a try). You are definitely starting in the wrong place with 8.04. Completely outdated, thoroughly obsolete, not secure (hasn't received security updates in two and a half years).

---

### Post by h.hittini on 2013-12-27
Thank you guys I will take the security issues into account
And just for reference I managed to install Ubuntu on the MicroSD using VMWare Workstation by creating a virtual machine and sitting the VM's hard disk to be a physical disk (the MicroSD connected to the laptop)
Thanks again for your efforts

---

### Post by claracc on 2013-12-28
You are very welcome

---

