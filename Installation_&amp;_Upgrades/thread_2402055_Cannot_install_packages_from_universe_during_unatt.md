---
title: "Cannot install packages from universe during unattended install of bionic 18.04"
date: 2018-09-25
forum: Installation &amp; Upgrades
---

### Post by josterma on 2018-09-25
Hi,

I am working on an unattended install of Bionic 18.04 using PXE and a preseed configuration file. During the installation I install a few packages (namely nscd, puppet, and ldap-auth-client) using pkgsel/include, and this worked well with Trusty 14.04, but those packages have since been moved from the 'main' repository to the 'universe' repository, which is now causing some problems.

```

d-i pkgsel/include string ldap-auth-client nscd puppet vlan nfs-common openssh-server lsb-release build-essential ethtool linux-image-extra-virtual

```

The installer doesn't appear to be using the 'bionic/universe' repository (as verified in the install logs) despite my configuration settings, causing the following error:

```

Sep 25 20:43:53 pkgsel: installing additional packages
Sep 25 20:43:53 in-target: Reading package lists...
Sep 25 20:43:53 in-target:
Sep 25 20:43:53 in-target: Building dependency tree...
Sep 25 20:43:53 in-target:
Sep 25 20:43:53 in-target: Reading state information...
Sep 25 20:43:53 in-target:
Sep 25 20:43:53 in-target: Package nscd is not available, but is referred to by another package.
Sep 25 20:43:53 in-target: This may mean that the package is missing, has been obsoleted, or
Sep 25 20:43:53 in-target: is only available from another source
Sep 25 20:43:53 in-target:
Sep 25 20:43:53 in-target: E
Sep 25 20:43:53 in-target: :
Sep 25 20:43:53 in-target: Unable to locate package ldap-auth-client
Sep 25 20:43:53 in-target:
Sep 25 20:43:53 in-target: E
Sep 25 20:43:53 in-target: :
Sep 25 20:43:53 in-target: Package 'nscd' has no installation candidate
Sep 25 20:43:53 in-target:
Sep 25 20:43:53 in-target: E
Sep 25 20:43:53 in-target: :
Sep 25 20:43:53 in-target: Unable to locate package puppet
Sep 25 20:43:53 in-target:

```

Note that I am using a mirror repository at "myhost.myinstitution.edu".

Relevant configuration snippets from preseed file:

```
### Mirror settings
d-i mirror/country string manual
d-i mirror/protocol string http
d-i mirror/http/hostname string myhost.myinstitution.edu
d-i mirror/http/directory string /apt/ubuntu
d-i mirror/suite string bionic
d-i mirror/udeb/suite string bionic


d-i apt-setup/services-select none
d-i apt-setup/security_host string myhost.myinstitution.edu
d-i apt-setup/security_path string /apt/ubuntu

d-i apt-setup/multiverse boolean true
d-i apt-setup/universe boolean true

```

I'm trying to figure out what magic configuration values, if any, will allow the installer process to use the bionic/universe repository. I had thought that using **d-i apt-setup/universe boolean true** would facilitate this, but it does not appear to be working.

Any advice appreciated.

Thanks,
Jory

---

