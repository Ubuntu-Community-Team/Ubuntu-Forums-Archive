---
title: "Upgrade Understanding"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by dsipe110 on 2018-06-06
Current OS: Ubuntu LTS 14.04

I have recently started using a patch manager for our primarily linux infrastructure and I have a few question regarding linux patching in general and what different commands include/classify upgrade types.

For instance, when i login I see the following notification.

46 packages can be updated.
28 updates are security updates.

My patch Manager only found two critical patches to be remediated, to which I deployed these remediations. Upon logging back in, the perviously mentioned update notice has disappeared. I expected this.
My question is when running the following command
sudo apt-get upgrade
There is still a lengthy list of things to upgrade.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libc-ares2 libgd2-xpm libv8-3.14.5 ruby-mysql
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-headers-server linux-image-generic
  linux-image-server linux-server
The following packages will be upgraded:
  apparmor apt apt-transport-https apt-utils cpp-4.8 curl dh-apparmor dpkg
  dpkg-dev g++-4.8 gcc-4.8 gcc-4.8-base ghostscript git git-core git-man
  ifupdown initramfs-tools initramfs-tools-bin isc-dhcp-client isc-dhcp-common
  kmod landscape-common libapparmor-perl libapparmor1 libapt-inst1.5
  libapt-pkg4.12 libasan0 libatomic1 libavahi-client3 libavahi-common-data
  libavahi-common3 libcups2 libcupsfilters1 libcupsimage2 libcurl3
  libcurl3-gnutls libdpkg-perl libelf1 libgcc-4.8-dev libgomp1 libgs9
  libgs9-common libgudev-1.0-0 libitm1 libkmod2 libmysqlclient-dev
  libmysqlclient18 libnginx-mod-http-auth-pam libnginx-mod-http-dav-ext
  libnginx-mod-http-echo libnginx-mod-http-geoip
  libnginx-mod-http-image-filter libnginx-mod-http-subs-filter
  libnginx-mod-http-upstream-fair libnginx-mod-http-xslt-filter
  libnginx-mod-mail libnginx-mod-stream libpam-systemd libperl5.18
  libplymouth2 libprocps3 libquadmath0 libssl-dev libssl-doc libssl1.0.0
  libstdc++-4.8-dev libstdc++6 libsystemd-daemon0 libsystemd-login0 libtasn1-6
  libtiff5 libtiff5-dev libtiffxx5 libtsan0 libudev1 libwayland-client0
  libwayland-cursor0 linux-libc-dev module-init-tools mysql-client
  mysql-client-5.5 mysql-client-core-5.5 mysql-common nginx nginx-common
  nginx-full nodejs openssh-client openssh-server openssh-sftp-server openssl
  patch perl perl-base perl-modules plymouth plymouth-theme-ubuntu-text procps
  python-apport python-crypto python-problem-report python-twisted-bin
  python-twisted-core python3-distupgrade python3-problem-report
  python3-update-manager resolvconf rsync sensible-utils systemd-services
  ubuntu-release-upgrader-core udev update-manager-core w3m wget yarn
117 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 80.8 MB of archives.
After this operation, 321 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Are these pending upgrades not displaying properly upon login? Are these just not considered security upgrades? I guess I don't fully understand how linux deploys their patches vs upgrades.

Thanks for any advice/knowledge.

---

### Post by rsteinmetz70112 on 2018-06-06
Running "apt-get update" updates the database and will generally show more upgrades than before running it. The login message shows what the system knows when logging in. Depending on your configuration the system, may do anything from waiting till you tell it to do something, updating the database periodically or upgrading everything automatically. 

Looking at the list you aren't running the latest kernel for you version. 

I'm curious why you decided only to upgrade the "critical patches". Many of the packages that are upgradeable may contain useful bug fixes and if you upgrade some and not others you could introduce incompatibilities. Many of these "fixes" are not security issues.

IF would be helpful if you gave a little more information about you installation including what Patch Manager you are using.  I've never found a reason form more that the supplied utilities such as apt, and dpkg.

---

### Post by dsipe110 on 2018-06-06
Thank you for the quick response!

1. "[COLOR=#000000]Looking at the list you aren't running the latest kernel for you version. [/COLOR]" I chose this server specifically for this reason, something I could watch and test upgrades on.
2. "[COLOR=#000000]I'm curious why you decided only to upgrade the "critical patches".[/COLOR]" Preferably I would like to upgrade everything from that command, the patch manger only found a few security updates. I wish it had upgraded all those packages to be honest.

Im using Ivanti Endpoint Security powered by heat. The reason for using this utility is primarily scalability. Im demoing products that can track patch management and remediation for a medium to large infrastructure. While apt and dpkg are very useful, they are still very manual.

---

### Post by rsteinmetz70112 on 2018-06-06
Generally Linux does not use discrete "patches", that is small pieces of software to designed to fix a single issue, such 'patches" are used by the upstream developers to update their code which is delivered downstream in "packages" that generally contain compiled binaries and the configuration information to install them correctly. Most packages also have parallel "source" packages that contain the full code allowing the user to compile their own. Unless I'm not understanding what you are saying. When a software package is updated the entire package is installed over the original package. The reasons for updating packages are many including, security, bugs, increased functionality to name a few. 

There are options which provide unattended upgrades and automatically download and install upgraded packages. I prefer to look at what is going to be installed before I do it and I'm always somewhat concerned a glitch with unattended operations will leave a remote system in a bad situation, so I prefer a semi-manual method. But then I don't run that many servers.

To upgrade all of the packages simply run "apt full-upgrade" and it will downland and install everything in the list, including the latest kernel. Sometimes it is necessary to reboot the server after an upgrade, usually when a new kernel is installed.  That is the reason the kernels are not included in the regular upgrades. When you install new packages there are options for installing recommended packages which are not exactly necessary but provide useful additional functions. 

The idea of the dpkg system (what apt and it relatives apt-get, aptitude and others use) is to keep the system up to date and consistent. Sometimes it probably upgrades things you don't really need to upgrade but partial upgrades can result in incompatibilities between packages.

There are methods of setting up things so only security updates are installed but that is something I don't do and am not competent to explain.

---

