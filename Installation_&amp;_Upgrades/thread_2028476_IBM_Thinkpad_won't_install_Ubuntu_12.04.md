---
title: "IBM Thinkpad won't install Ubuntu 12.04"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by yesterdayman on 2012-07-18
Trying to install Ubuntu Desktop 12.04 32-bit on IBM Thinkpad T42.  Already have it installed and running on same machine as dual boot with Windows, was installed using Windows Installer.

Now I have decided I don't need Windows, so created a bootable USB stick from ISO download, tried to boot from USB stick, and install was terminated with the following message:

"This kernel requires the following features not present on the CPU: pae
Unable to boot - please use a kernel appropriate for your CPU."

Logically this just doesn't make sense.  Ubuntu runs on this machine when installed from Windows Installer, but not when trying to install from bootable USB stick of same version.  I am no Linux guru so now I'm stuck.  Any ideas?

---

### Post by steeldriver on 2012-07-18
iirc as of 12.04 the standard desktop-386 iso no longer contains a non-pae kernel - perhaps the Windows installer does? 

you can either use the 'alternate' iso image or try Xubuntu 12.04 (which will install non-pae by default) - that's what I have on my old X30 Thinkpad - or Lubuntu

---

