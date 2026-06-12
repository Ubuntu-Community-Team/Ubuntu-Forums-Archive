---
title: "Update source files not found 404"
date: 2023-09-18
forum: Installation &amp; Upgrades
---

### Post by rkrite on 2023-09-18
Hi,

I am running Kubuntu 22.04.3 LTS x86_64.

When I run "```
sudo apt-get upgrade
```", I am getting the following errors...


```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gjs libgjs0g linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04 linux-image-generic-hwe-22.04
The following packages will be upgraded:
  libc-bin libc-dev-bin libc-devtools libc6 libc6:i386 libc6-dbg libc6-dev libnss-systemd libpam-systemd libsystemd0 libudev1 linux-libc-dev locales openssh-client openssh-server
  openssh-sftp-server systemd systemd-oomd systemd-sysv systemd-timesyncd thermald udev
22 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
Need to get 1,330 kB/37.2 MB of archives.
After this operation, 3,072 B disk space will be freed.
Do you want to continue? [Y/n] y
Err:1 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-84.93
  404  Not Found [IP: 202.158.214.106 80]
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.15.0-84.93_amd64.deb  404  Not Found [IP: 202.158.214.106 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

When I investigate  [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux/) I see that the files actually do not exist.

Is there something in my course list that might be looking for wrong file versions?

Thanks

---

### Post by MAFoElffen on 2023-09-18
That update hit me from us.archive.ubuntu.com/ubuntu 2 days ago. Probaly just a delay in the repo sync's. I wold wait a bit, then do
```

sudo apt install -f

```
...as it recommended to fix the dependencies.

---

### Post by rkrite on 2023-09-19
Wonderful. This has worked for me. Thanks very much.

---

