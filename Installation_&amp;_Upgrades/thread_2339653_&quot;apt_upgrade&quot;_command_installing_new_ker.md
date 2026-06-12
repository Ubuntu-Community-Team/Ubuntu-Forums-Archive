---
title: "&quot;apt upgrade&quot; command installing new kernel image"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by Only1KW on 2016-10-11
Just now, I am trying to upgrade the packages on my 16.04 installation.  When I run "apt upgrade", new kernel images are listed as being scheduled to be installed.  If I run "apt dist-upgrade" I get the same output.  If I run "apt-get upgrade", then the kernel images are held back.  Is apt working as expected?  I thought I was supposed to be using apt now instead of apt-get, but I also thought apt was supposed to run mostly the same as apt-get.  If this is expected behavior, I plan to continue using apt-get.

```

$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-image-4.4.0-42-generic linux-image-extra-4.4.0-42-generic
The following packages will be upgraded:
  bcompare cmake cmake-data dkms git git-man google-chrome-stable gtk2-engines-murrine ifupdown init init-system-helpers initramfs-tools
  initramfs-tools-bin initramfs-tools-core isc-dhcp-client isc-dhcp-common klibc-utils libklibc libnm0 libpython3.5 libpython3.5-minimal
  libpython3.5-stdlib linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev network-manager python3.5
  python3.5-minimal qemu-block-extra qemu-utils snap-confine snapd ubuntu-core-launcher ubuntu-drivers-common xserver-common xserver-xorg-core
38 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 193 MB of archives.
After this operation, 297 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-image-4.4.0-42-generic linux-image-extra-4.4.0-42-generic
The following packages will be upgraded:
  bcompare cmake cmake-data dkms git git-man google-chrome-stable gtk2-engines-murrine ifupdown init init-system-helpers initramfs-tools
  initramfs-tools-bin initramfs-tools-core isc-dhcp-client isc-dhcp-common klibc-utils libklibc libnm0 libpython3.5 libpython3.5-minimal
  libpython3.5-stdlib linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev network-manager python3.5
  python3.5-minimal qemu-block-extra qemu-utils snap-confine snapd ubuntu-core-launcher ubuntu-drivers-common xserver-common xserver-xorg-core
38 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 193 MB of archives.
After this operation, 297 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
$ uname -a
Linux robo 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  bcompare cmake cmake-data dkms git git-man google-chrome-stable gtk2-engines-murrine ifupdown init init-system-helpers initramfs-tools
  initramfs-tools-bin initramfs-tools-core isc-dhcp-client isc-dhcp-common klibc-utils libklibc libnm0 libpython3.5 libpython3.5-minimal
  libpython3.5-stdlib linux-firmware linux-libc-dev network-manager python3.5 python3.5-minimal qemu-block-extra qemu-utils snap-confine snapd
  ubuntu-core-launcher ubuntu-drivers-common xserver-common xserver-xorg-core
35 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 125 MB of archives.
After this operation, 1,284 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by deadflowr on 2016-10-11
Yes it's working exactly how it is expected to work.
apt and apt-get run differently for a few things.
apt-get with just upgrade holds back packages that need to install new packages, like new kernels as new kernels install new dependencies.
apt with upgrade will install those new packages but will not remove anything from the system.
apt full-upgrade will install those new packages, but will also remove packages if the new package require that an older package be removed.

I would assume apt dist-upgrade runs as it does as apt-get dist-upgrade.

---

### Post by Only1KW on 2016-10-11
Is there a document which lists this difference?  I googled "apt vs apt-get" and looked at the first few pages suggested, and none of them listed this difference.

Are there arguments I can pass to apt to get the same behavior as "apt-get upgrade"?  I read that apt-get might go away in the future and would hate to lose the ability to upgrade the majority of packages on my system without having to reboot afterwards.

---

### Post by deadflowr on 2016-10-11
> Is there a document which lists this difference? I googled "apt vs apt-get" and looked at the first few pages suggested, and none of them listed this difference.

The differences are slight, and if you don't pay attention, you might miss them.
look at both the man pages for apt and apt-get.
from apt:
```
upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to
           statisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the remove of an installed
           package the upgrade for this package isn't performed.

```

and from man apt-get:
```
upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

```

> Are there arguments I can pass to apt to get the same behavior as "apt-get upgrade"? 

Not sure, but as the apt man pages states from the get-go, it is not an exhaustive and thorough listing of all features:
```
Much like apt itself, its manpage is intended as an end user interface
       and as such only mentions the most used commands and options partly to
       not duplicate information in multiple places and partly to avoid
       overwhelming readers with a cornucopia of options and details.

```

So perhaps there is a simple command like safe-upgrade that works as you would want it to.

Edit: no safe-upgrade command for apt.
I guess you would probably need to look through the list of options apt-get has, as apt-get options do transfer over to apt (like --reinstall does)

Extra edit: Try:
```
sudo apt upgrade --only-upgrade
```

Another edit: Oh, nevermind, that seems to want to install everything as well...
Time to dig some more.

---

### Post by Only1KW on 2016-10-20
I found another way to "keep back" packages:

```
sudo apt-mark hold package_name
sudo apt-mark unhold package_name
```

Unfortunately, the "hold" operation does not appear to have been ported to apt.  But if apt-get goes away and apt-mark does not, it may be a reasonable alternative to prevent kernels and other packages requiring restart from being installed if not desired.

---

### Post by Impavidus on 2016-10-21
Using **apt-get upgrade** instead of **apt upgrade** will block most kernel upgrades, but not all upgrades that require a restart. If you install an upgrade that requires a restart, you don't have to restart immediately. You can wait for the next morning, if you wish.

---

