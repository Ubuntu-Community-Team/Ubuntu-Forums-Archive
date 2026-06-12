---
title: "Error while unpacking linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb"
date: 2019-06-20
forum: Installation &amp; Upgrades
---

### Post by superian on 2019-06-20
The recent update to kernel 5.0.0-17 is causing problems on one PC here.

Specifically, no matter if it is deleted and downloaded again, apt-get and dpkg have an error when dealing with /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb and this leaves 5.0.0-17 useless, because it has no network connectivity or mouse drivers available. (Fortunately, the keyboard still works, so it's possible to reboot and select 5.0.0-16 instead.

**Interestingly, the error is with a different module each time**, for example:

```
ian@example$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.0.0-15 linux-headers-5.0.0-15-generic
  linux-image-5.0.0-15-generic linux-modules-5.0.0-15-generic
  linux-modules-extra-5.0.0-15-generic linux-tools-5.0.0-15
  linux-tools-5.0.0-15-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-5.0.0-17-generic
The following NEW packages will be installed
  linux-modules-extra-5.0.0-17-generic
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
Need to get 33.2 MB of archives.
After this operation, 173 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu disco-updates/main amd64 linux-modules-extra-5.0.0-17-generic amd64 5.0.0-17.18 [33.2 MB]
Fetched 33.2 MB in 8s (4,392 kB/s)                                             
(Reading database ... 402016 files and directories currently installed.).....................] 
Preparing to unpack .../linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-modules-extra-5.0.0-17-generic (5.0.0-17.18) ..................................................................................] 
[B]dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb (--unpack):
 unable to open '/lib/modules/5.0.0-17-generic/kernel/drivers/net/ethernet/aquantia/atlantic/atlantic.ko.dpkg-new': Operation not permitted[/B]
Segmentation fault
ian@example:~$
```

OK, try again:

```
ian@example:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  intel-microcode iucode-tool linux-headers-5.0.0-15 linux-headers-5.0.0-15-generic linux-image-5.0.0-15-generic linux-modules-5.0.0-15-generic
  linux-modules-extra-5.0.0-15-generic linux-tools-5.0.0-15 linux-tools-5.0.0-15-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-5.0.0-17-generic linux-modules-5.0.0-17-generic linux-modules-extra-5.0.0-17-generic
Suggested packages:
  fdutils linux-doc-5.0.0 | linux-source-5.0.0 linux-tools linux-headers-5.0.0-17-generic
The following NEW packages will be installed
  linux-image-5.0.0-17-generic linux-modules-5.0.0-17-generic
The following packages will be upgraded:
  linux-modules-extra-5.0.0-17-generic
1 to upgrade, 2 to newly install, 0 to remove and 15 not to upgrade.
1 not fully installed or removed.
Need to get 22.1 MB/55.3 MB of archives.
After this operation, 250 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu disco-updates/main amd64 linux-modules-5.0.0-17-generic amd64 5.0.0-17.18 [13.7 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu disco-updates/main amd64 linux-image-5.0.0-17-generic amd64 5.0.0-17.18 [8,353 kB]
Fetched 22.1 MB in 5s (4,066 kB/s)                        
Selecting previously unselected package linux-modules-5.0.0-17-generic.
(Reading database ... 371577 files and directories currently installed.)
Preparing to unpack .../linux-modules-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-modules-5.0.0-17-generic (5.0.0-17.18) ...
Selecting previously unselected package linux-image-5.0.0-17-generic.
Preparing to unpack .../linux-image-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-image-5.0.0-17-generic (5.0.0-17.18) ...
Preparing to unpack .../linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-modules-extra-5.0.0-17-generic (5.0.0-17.18) over (5.0.0-17.18) ...
[B]dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb (--unpack):
 unable to open '/lib/modules/5.0.0-17-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko.dpkg-new': Operation not permitted[/B]
Segmentation fault
ian@example:~
```

OK, let's try installing it directly from the .deb file:

```
ian@example:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb
(Reading database ... 372860 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-modules-extra-5.0.0-17-generic (5.0.0-17.18) over (5.0.0-17.18) ...
[B]dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb (--install):
 unable to open '/lib/modules/5.0.0-17-generic/kernel/drivers/infiniband/hw/ocrdma/ocrdma.ko.dpkg-new': Operation not permitted[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb
ian@example:~$
```

OK, let's try installing it from somewhere else:

```
ian@example:~$ sudo cp /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb .
ian@example:~$ sudo dpkg -i --force-overwrite linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb
(Reading database ... 372860 files and directories currently installed.)
Preparing to unpack linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-modules-extra-5.0.0-17-generic (5.0.0-17.18) over (5.0.0-17.18) ...
[B]dpkg: error processing archive linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb (--install):
 unable to open '/lib/modules/5.0.0-17-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko.dpkg-new': Operation not permitted[/B]
Errors were encountered while processing:
 linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb
ian@example:~$ 
```

It doesn't seem to be a disc space issue:

```
ian@example:~$ df -lh
Filesystem      Size  Used Avail Use% Mounted on
udev            7.5G     0  7.5G   0% /dev
tmpfs           1.5G  3.1M  1.5G   1% /run
/dev/sda6        32G   17G   14G  55% /
tmpfs           7.5G  102M  7.4G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.5G     0  7.5G   0% /sys/fs/cgroup
/dev/sda7       198G  183G  4.3G  98% /home
tmpfs           1.5G   68K  1.5G   1% /run/user/1001
tmpfs           1.5G     0  1.5G   0% /run/user/1000

```

What else should I try?

---

### Post by tehtubez on 2019-06-21
I have this same issue as well. Commenting to follow.

```
$ sudo apt --fix-broken installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.0.0-17-generic
The following NEW packages will be installed:
  linux-modules-extra-5.0.0-17-generic
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
7 not fully installed or removed.
Need to get 0 B/33.2 MB of archives.
After this operation, 173 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 208677 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb ...
Unpacking linux-modules-extra-5.0.0-17-generic (5.0.0-17.18) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb (--unpack):
 unable to open '/lib/modules/5.0.0-17-generic/kernel/drivers/media/dvb-frontends/tda10023.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.0.0-17-generic_5.0.0-17.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by tehtubez on 2019-06-21
Hey this fixed my issue as it appears my AV was causing the problem. If you have AV disable it and try again.


[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1739991/]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1739991/comments/3")
> [COLOR=#333333][FONT=monospace]I think the problem was caused by sophos antivirus. After deactivating the on-demand scan with[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sudo /opt/sophos-av/bin/savdctl disable[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I had no problems.[/FONT][/COLOR]

---

### Post by superian on 2019-06-23
Thank you - yes, this machine has sav-protect installed.

---

