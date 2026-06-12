---
title: "Kubuntu 13.10 alternate cd ?"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by jigar2 on 2014-01-27
Hi
I have many problems on my Hybrid Graphics system running Kubuntu 12.04 with a radeon 8670A graphics card. Basically I have tried installing fglrx,fglrx-updates and the xorg-edgers driver through multiple guides but am unable to run Catalyst Centre. It gives an error that no driver is installed. So I cant switch to High Performance graphics at all.
I have tried the 13.10 live cd and it shows a black screen after the kubuntu logo. I think maybe xserver crashes or maybe this is a graphics driver related problem.

Is there an alternate Kubuntu 13.10 cd out there as maybe Catalyst Centre will work over there.

---

### Post by mörgæs on 2014-01-28
Hi, welcome to the fora.

In a sad chain of events the alternate ISO's were shut down for everything except Lubuntu. The closest option is the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"), from which you can install the Kubuntu and other desktops.

---

### Post by mastablasta on 2014-01-28
have you tried 13.10 and then use nomodeset boot option?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sudodus on 2014-01-31
You could try the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") in text mode, and install from one of the tarballs

```
Kubuntu_13.10oem-nov23.tar.xz          # OEM: ready for the end user
KubuntuPrecise.tar.xz
```

At reboot after installation, you can use the [boot option]("https://help.ubuntu.com/community/BootOptions") ***nomodeset*** and/or ***text*** in the grub menu and get it running well enough to install a proprietary driver.

---

