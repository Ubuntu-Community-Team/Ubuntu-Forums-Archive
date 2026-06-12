---
title: "[LUKS] Updating the kernel"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by Sariel Amraphel on 2007-02-22
It seems the updating of the kernel isn't allowed when having an LUKS encrypted root and swap...
The installation method I used was: 
- Ubuntu edgy server with an install CD
- [http://johnleach.co.uk/words/archives/2006/12/06/245/](http://johnleach.co.uk/words/archives/2006/12/06/245/)
- XUbuntu and Ubuntu edgy desktop with the net

I get the following error message:
> 
Setting up linux-image-2.6.17-11-server (2.6.17.1-11.35) ...
Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version 
2.6.17-11-server on running kernel 2.6.17-10-server in /usr/sbin/mkinitramfs
dpkg: error processing linux-image-2.6.17-11-server (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.17-11-server; however:
  Package linux-image-2.6.17-11-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server; however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured


I've noticed other people have found this problem too, with someone suggesting to do a forced upgrade/reconfigure, but this hasn't helped.

I've gotten mkinitramfs to create a new ramfs for the 2.6.17-11 kernel (which I can boot and have booted), but apt-get, aptitude and dpkg keep on whining about the kernel not being configured.

Any idea how I can stop this annoying complaining about the supposedly unconfigured kernel?

---

