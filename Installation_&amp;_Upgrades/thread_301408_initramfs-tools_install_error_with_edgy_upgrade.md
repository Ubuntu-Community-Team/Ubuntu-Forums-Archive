---
title: "initramfs-tools install error with edgy upgrade"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by pvanheus on 2006-11-17
I'm trying to upgrade to edgy using apt-get (update, dist-upgrade, -f install, etc). I've run into a problem with initramfs-tools, though:

root@this106:/var/tmp # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following NEW packages will be installed:
  initramfs-tools
0 upgraded, 1 newly installed, 0 to remove and 521 not upgraded.
1 not fully installed or removed.
Need to get 0B/50.1kB of archives.
After unpacking 356kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 66318 files and directories currently installed.)
Unpacking initramfs-tools (from .../initramfs-tools_0.69ubuntu20_all.deb) ...
sed: can't read -: No such file or directory
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm not sure what is happening inside the unpack process that is causing this error. Does anyone have ideas?

Thanks!
Peter

---

### Post by AgenT on 2006-11-19
Try:
Get the newest version of initramfs-tools from the ftp:
(note: some steps will error)
```
apt-get -f install
wget  http://ftp.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.69ubuntu20_all.deb
dpkg -i initramfs-tools_0.69ubuntu20_all.deb
apt-get install cpio
apt-get -f install
```

---

