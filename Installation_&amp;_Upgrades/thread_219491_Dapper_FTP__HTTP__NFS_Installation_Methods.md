---
title: "Dapper FTP / HTTP / NFS Installation Methods"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by vprasad on 2006-07-20
Anyone know how to get an FTP or HTTP or NFS LAN installation started on Ubuntu? I can do NFS installs with Slackware; I can do FTP or HTTP or NFS installs with just about any other distribution (SuSe, Redhat, Debian, etc)... but I can't figure out how to get it going on Ubuntu-- is there a special disk or special set of procedures I need to get going?

I've tried the Mini Netboot disk, but it does not provide an option for me to use a local (on my LAN) server... I'm stuck pulling files off of the internet for every attempt at installing.

---

### Post by iamwu on 2006-07-20
> **vprasad said:**
> Anyone know how to get an FTP or HTTP or NFS LAN installation started on Ubuntu? I can do NFS installs with Slackware; I can do FTP or HTTP or NFS installs with just about any other distribution (SuSe, Redhat, Debian, etc)... but I can't figure out how to get it going on Ubuntu-- is there a special disk or special set of procedures I need to get going?

I've tried the Mini Netboot disk, but it does not provide an option for me to use a local (on my LAN) server... I'm stuck pulling files off of the internet for every attempt at installing.

I suggest mirroring the Ubuntu mirror to a system on your internal lan, then point your netboot configuration files at this local server.  The apt-mirror tool is sufficient to do this.

see:
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

- Will

---

### Post by vprasad on 2006-07-20
Will, unfortunately, one of the environments I'll be working in does not have PXE capable NICs.  Any way to do an FTP / HTTP or NFS install of Dapper?

---

