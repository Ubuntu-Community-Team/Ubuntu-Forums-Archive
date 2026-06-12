---
title: "Distribute ubuntu using PXE?"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by ftornell on 2011-04-26
Hi,
Is there any good way of distribution a ubuntu installation on workstations using PXE?

And is it possible to pre-configure the installation with various settings?

---

### Post by AllGamer on 2011-04-26
> **ftornell said:**
> Hi,
Is there any good way of distribution a Ubuntu installation on workstations using PXE?

And is it possible to pre-configure the installation with various settings?

sounds like you are looking up the same thing i was working on.

yes you can definitely pre-configure Ubuntu for corporate distribution over the network

check out live cd customization [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

it basically deploys with whatever you configure it to do so.

i also found another less clean method, which will really deploy exactly what you changed, but it's not a good clean solution for a network environment, but it's great for mirroring the same setup on a few machines.

in regards to Network boot distro via PXE, just configure the PXE server to push out the install or .iso from a remote share

just Google up PXE & Linux push, and you will find these 2 great guides which i used for my own reference

[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)
[http://linux-sxs.org/internet_serving/pxeboot.html](http://linux-sxs.org/internet_serving/pxeboot.html)

---

### Post by boethius on 2011-04-27
> **ftornell said:**
> Hi,
Is there any good way of distribution a ubuntu installation on workstations using PXE?

And is it possible to pre-configure the installation with various settings?
While the newer versions of memdisk (the COM32 binary that is part of the syslinux package, which also includes the pxelinux network bootstrap) allows you to boot large ISOs, I wouldn't recommend this as a way of installing Ubuntu - or any OS, really - over the network using PXE.  The two big issues are, one, the full ISO is large and takes a long time to boot over the network and, two, the information that allows you to preseed the install settings would have to be bundled with the ISO - which means you'd have to modify the ISO and re-create it every time you made a change to the pre-install settings.  And, trust me, setting up an Ubuntu pre-seed file is a non-trivial task that usually takes several iterations before you get it all the way you want it to be.  Better to have your install files stored on an HTTP server location that the preseed will source and have the preseed file itself located on an HTTP URL also so the process of tweaking and tuning it is much, much easier. 

I would refer to the following URLs for a general starter on how to get going with Ubuntu PXE installs:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

[http://www.debuntu.org/book/export/html/193](http://www.debuntu.org/book/export/html/193)

[https://www.digisoftinc.org/wiki/index.php/Ubuntu_preseed.cfg_installs_off_PXE_Boot](https://www.digisoftinc.org/wiki/index.php/Ubuntu_preseed.cfg_installs_off_PXE_Boot)

Preseeding is the trickiest part as the preseed semantics tend to change a bit from one version of the OS to the next.  All a preseed is is a response / answer file to the menu options normally presented when you install Ubuntu manually.  Matching those up to the present version can be fun and will probably require you to verify that a version you create say for version 10.04 still works for 10.10 and still works for 11, etc.  

You may want to look at what solutions are available for more complete systems config and OS deployment automation rather than rolling your own.  Yes, it's nice to learn about the nuts and bolts of how it all actually works - and maybe it's a worthwhile endeavor to do a bit of it yourself just to learn, but I would look around at the different tools that are out there.  Off the top of my head I'd say look at LinuxCOE, OpenQRM, UDA (ultimate deployment appliance - geared for VMware environments), NOC-PS (commercial, per deployed server licensing).  There are big commercial solutions of course like Altiris, KACE, but those are bucks and probably not appropriate for what you need, but if you're in an environment where you want some supportability for your deployment platform, you may want to look at those as well.

---

### Post by ftornell on 2011-05-12
Hi again!

I was following this guide [http://www.howtoforge.com/ubuntu_pxe_install_server]("http://www.howtoforge.com/ubuntu_pxe_install_server")

But the guide is kind of old and it might be new ways or new packages needed?

I'm running Ubuntu Server 11.04 and want do distribute Ubuntu Desktop 11.04 x86.

But...

- when following the guide i can't install netkit-inetd, it can't be found.
- dhcp3-server can be installed but it seems there already are a dhcp server installed but not active? (I did not choose to install DHCP during the ubuntu server installation)

I can find the dhcpd.conf file in /etc/dhcpd/ folder - not /etc/dhcp3/ as the guide states.

So is this dhcp3-server not needed?

How about inetd?

Any tips appreciated!

---

### Post by zuffi on 2011-05-12
The package "dhcp3" moved to "dhcp" from 10.x to 11.04. 

Take a look at 
```
/etc/init.d/
```the names of the startup-scripts changed too

---

