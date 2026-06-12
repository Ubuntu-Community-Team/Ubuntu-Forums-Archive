---
title: "Systemd-Resolved Error After Upgrade to 22.10"
date: 2022-11-03
forum: Installation &amp; Upgrades
---

### Post by bigverm23 on 2022-11-03
[HTML]Setting up systemd-resolved (251.4-1ubuntu7) ...Converting /etc/resolv.conf to a symlink to /run/systemd/resolve/stub-resolv.conf...cp: '/etc/resolv.conf' and '/run/systemd/resolve/stub-resolv.conf' are the same filedpkg: error processing package systemd-resolved (--configure): installed systemd-resolved package post-installation script subprocess returned error exit status 1Errors were encountered while processing: systemd-resolvedneedrestart is being skipped since dpkg has failedE: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]

Subsequently, I can not run apt update or apt install for any new packages.  How do I go about resolving this?

---

### Post by SeijiSensei on 2022-11-03
sudo rm /etc/resolv.conf 

On my 22.04 system, /etc/resolv.conf is the symlink referenced above. I'd try deleting the file or link on your system so the installer can restore it.

If you've created a custom resolv.conf, you should instead edit /etc/systemd/resolved.conf and put any server or domain declarations there. Then run "sudo systemctl restart systemd-resolved".

---

### Post by bigverm23 on 2022-11-03
> **SeijiSensei said:**
> sudo rm /etc/resolv.conf 

On my 22.04 system, /etc/resolv.conf is the symlink referenced above. I'd try deleting the file or link on your system so the installer can restore it.

If you've created a custom resolv.conf, you should instead edit /etc/systemd/resolved.conf and put any server or domain declarations there. Then run "sudo systemctl restart systemd-resolved".

It's likely because I'm using Adguard-Home as whole home dns so my /etc/resolv.conf looks like
```
nameserver 127.0.0.1nameserver 10.0.0.7
nameserver 1.1.1.1

```
and my /etc/systemd/resolved.conf.d/adguardhome.conf looks like
```
DNS=127.0.0.1
DNSStubListener=no

```

---

