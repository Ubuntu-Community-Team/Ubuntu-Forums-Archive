---
title: "Can't install Ubuntu 11.10 Server - linux-headers-server dependency issue?"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by victorhooi on 2011-12-20
Hi,

I'm attempting to install Ubuntu 11.10 Server (AMD64) on a VMWare ESXi virtual machine.

When I get to the installing packages stage, it errors out:

```
Installation Step Failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software.
```

I've checked the CD-ROM, Ubuntu reports it as a valid CD-ROM.

If I look at /var/log/syslog, I see:

```
Unet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dpkg: dependency problems prevent configuration of linux-headers-server:
linux-headers-server depends on linux-headers-3.0.0-12-server; however:
Package linux-headers 3.0.0-12-server is not installed.
dpkg: error processing linux-headers-server (--configure):
dependency problems - leaving uncofigured
...
WARNING **: Configuring 'pkgsel' failed with error code 100
WARNING **: Menu item 'pkgsel' failed.
```

This is just running through the installation wizard, albeit behind a HTTP proxy. I'm still not sure what would cause this issue? I was under the impression that 11.10 Server was a stable GA release of Ubuntu?

Cheers,
Victor

---

### Post by MAFoElffen on 2011-12-20
> **victorhooi said:**
> Hi,

I'm attempting to install Ubuntu 11.10 Server (AMD64) on a VMWare ESXi virtual machine.

When I get to the installing packages stage, it errors out:

```
Installation Step Failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software.
```I've checked the CD-ROM, Ubuntu reports it as a valid CD-ROM.

If I look at /var/log/syslog, I see:

```
Unet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dpkg: dependency problems prevent configuration of linux-headers-server:
linux-headers-server depends on linux-headers-3.0.0-12-server; however:
Package linux-headers 3.0.0-12-server is not installed.
dpkg: error processing linux-headers-server (--configure):
dependency problems - leaving uncofigured
...
WARNING **: Configuring 'pkgsel' failed with error code 100
WARNING **: Menu item 'pkgsel' failed.
```This is just running through the installation wizard, albeit behind a HTTP proxy. I'm still not sure what would cause this issue? I was under the impression that 11.10 Server was a stable GA release of Ubuntu?

Cheers,
Victor
I don't know if VMWare is adding to that... I don't do that.

I do know that I have 4 servers up on 11.10, 1 on 12.10.  Done dozens of installs of server 11.10.  

No errors in dmesg on downloading packages?  Like a proxy problem? Did you try reinstalling?

---

### Post by victorhooi on 2011-12-27
Hi,

Hmm, well, it could have been an intermittent thing, or it might have been related to BTRFS - not sure.

I was originally installing over some BTRFS partitions that had been created before - however, I switched to using Guided Partitioning, using the default ext4 partitions, and it seems to work fine.

Only other possibly explanation was that it was a intermittent network thing, but that wouldn't explain the weird dependency bug...

I mean, if nobody else has ever heard/seen this sort of thing, I'll chalk it up to cosmic rays, or wind in the data centre...lol, and it seems happy enough now.

Cheers,
Victor

---

