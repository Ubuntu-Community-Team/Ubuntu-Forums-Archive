---
title: "401 Authentication Error When Install/updating Software"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by reddingbacon on 2012-09-12
When running apt-get install | update (or update-manager) I get Authentication Errors for multiple packages.  Following is an example trying to install openssh-server:

```
$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ssh-import-id
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra monkeysphere
The following NEW packages will be installed:
  openssh-server ssh-import-id
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 348 kB of archives.
After this operation, 891 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  openssh-server ssh-import-id
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com/ubuntu/ precise/main openssh-server i386 1:5.9p1-5ubuntu1
  401  Authorization Required [IP: 91.189.92.156 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main ssh-import-id all 2.10-0ubuntu1
  401  Authorization Required [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_5.9p1-5ubuntu1_i386.deb  401  Authorization Required [IP: 91.189.92.156 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/ssh-import-id/ssh-import-id_2.10-0ubuntu1_all.deb  401  Authorization Required [IP: 91.189.92.156 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```I've been through multiple forums for a day now and tried many things.  Same issue for Gimp package, which I uninstalled and re-installed to solve the problem for it, but I don't understand the overall problem here.

Thanks a bunch,
Redding

---

### Post by reddingbacon on 2012-09-12
Company firewall configuration had changed.  Once corrected I was able to connect and update.

- Redding

---

