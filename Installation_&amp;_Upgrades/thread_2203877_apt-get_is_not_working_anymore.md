---
title: "apt-get is not working anymore"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by jose21 on 2014-02-05
I have no idea how this even started. I want to install PHP-curl but I get the same error no matter what I am trying to install:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 mbr
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common debianutils friendly-recovery hostname ifupdown initramfs-tools
  initramfs-tools-bin initscripts libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libbsd0 libcap2
  libdb5.1 libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libedit2 libffi6 libglib2.0-0 libgssapi-krb5-2 libk5crypto3
  libkrb5-3 libkrb53 libkrb5support0 libnih-dbus1 libnih1 libpciaccess0 libpcre3 libplymouth2 libssl1.0.0 libtinfo5 libudev0
  mountall openssh-client openssh-server plymouth sensible-utils sysvinit-utils udev upstart util-linux util-linux-locales
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom isc-dhcp-client dhcp-client rdnssd php-pear krb5-doc krb5-user ssh-askpass
  libpam-ssh keychain monkeysphere openssh-blacklist openssh-blacklist-extra rssh molly-guard sash watershed graphviz
Recommended packages:
  ssl-cert php5-cli libglib2.0-data shared-mime-info krb5-locales xauth ssh-import-id plymouth-theme-ubuntu-text plymouth-theme
The following packages will be REMOVED
  eject libdevmapper1.02.1 lilo startup-tasks system-services upstart-compat-sysv upstart-logd
The following NEW packages will be installed
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common initramfs-tools-bin libapache2-mod-php5 libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libbsd0 libcap2 libdb5.1 libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libffi6
  libglib2.0-0 libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 libnih-dbus1 libnih1 libpciaccess0 libpcre3 libplymouth2
  libssl1.0.0 libtinfo5 libudev0 mountall php5-curl plymouth sensible-utils sysvinit-utils
The following packages will be upgraded:
  debianutils friendly-recovery hostname ifupdown initramfs-tools initscripts libedit2 libkrb53 openssh-client openssh-server udev
  upstart util-linux util-linux-locales
14 upgraded, 36 newly installed, 7 to remove and 101 not upgraded.
Need to get 0B/12.2MB of archives.
After this operation, 23.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Couldn't configure pre-depend upstart-job for hostname, probably a dependency cycle.

```

---

### Post by Frogs Hair on 2014-02-05
Try the following and attempt the installation again.


```
sudo apt-get autoremove
``` ```
sudo apt-get update
```e

---

