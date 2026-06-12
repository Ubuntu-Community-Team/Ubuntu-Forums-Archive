---
title: "unattended install with PXE server and kickstart"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Zafrusteria on 2011-06-19
Hi,

I would like to be able to setup unattended installations of Ubuntu using a PXE server and kickstart to create Virtualbox machines. I have read and followed this post (by far the most complete)  [https://help.ubuntu.com/community/PXEInstallServer]("https://help.ubuntu.com/community/PXEInstallServer").

The problem is that although Ubuntu runs through the installation process, what is created is, well pretty much useless :(.  I say useless because  it will not boot. Even using the really minimal kickstart script from the post above results in a non booting system. 

```
install
url --url http://192.168.0.1/ubuntu/
```

there is no grub menu or message but I do see the purple loader page flash on the screen for a few ms. 

If I mount the created HD as a second drive to a working machine and look at the contents there appears to be a system installed and I can boot this in safe mode with some messing around, but nothing else. I believe the problem is the way the installer is using the kickstart script and then failing to configure, grub, and or the boot / root partitions. e.g. None of the partitions are aligned to cylinder boundaries. 

[LIST]
[*]I already, have a working PXE server that I can use with kickstart scripts to install Fedora as VirtualBox guests. Works a treat :D
[*]I can hand install Ubuntu 11.04 as a guest on VirtualBox.
[*]I have tried using the kickstart script from the Ubuntu package system-config-kickstart.
[/LIST]
There are a number of "other" posts I have read. Most of them are old, incomplete or still a work in progress. The official documentation is no better. 

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
[http://ubuntuforums.org/showthread.php?t=818721](http://ubuntuforums.org/showthread.php?t=818721)
[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)
[https://help.ubuntu.com/10.04/installation-guide/i386/automatic-install.html](https://help.ubuntu.com/10.04/installation-guide/i386/automatic-install.html)

I am assuming this is possible as Ubuntu desktop and server are being pushed as an IT  solution for business. I cannot see how this is possible without unattended installs.

---

