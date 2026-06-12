---
title: "Installing openvpn on ubuntu 12.10"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by sudha2 on 2014-12-31
I am trying to install openvpn on ubuntu and when i run  apt-get i get the following error

```
sudo apt-get install openvpnReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-ares-dev libev-dev libjs-node-uuid libssl-dev libssl-doc libv8-dev
  node-abbrev node-block-stream node-fstream node-graceful-fs node-inherits
  node-ini node-lru-cache node-minimatch node-mkdirp node-node-uuid node-nopt
  node-request node-rimraf node-semver node-tar node-which zlib1g-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liblzo2-2 libpkcs11-helper1
The following NEW packages will be installed:
  liblzo2-2 libpkcs11-helper1 openvpn

0 upgraded, 3 newly installed, 0 to remove and 168 not upgraded.
Need to get 547 kB of archives.
After this operation, 1,397 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  liblzo2-2 libpkcs11-helper1 openvpn
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main liblzo2-2 amd64 2.06-1build1
  404  Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main libpkcs11-helper1 amd64 1.09-1build1
  404  Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main openvpn amd64 2.2.1-8ubuntu2.1
  404  Not Found [IP: 91.189.91.24 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lzo2/liblzo2-2_2.06-1build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lzo2/liblzo2-2_2.06-1build1_amd64.deb)  404  Not Found [IP: 91.189.91.24 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pkcs11-helper/libpkcs11-helper1_1.09-1build1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pkcs11-helper/libpkcs11-helper1_1.09-1build1_amd64.deb)  404  Not Found [IP: 91.189.91.24 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.2.1-8ubuntu2.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.2.1-8ubuntu2.1_amd64.deb)  404  Not Found [IP: 91.189.91.24 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```


I am able to login to us.archive.ubuntu.com via the browser and i get the directory index and on checking the "quantal" directory is nonexistent How to resolve this?

---

### Post by yancek on 2014-12-31
As you can see at the Ubuntu link below, support for 12.10 ended in May, 2014.  

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Impavidus on 2015-01-01
Which means the repositories have been removed from that server and are no longer kept up to date. Your best option is to do a clean install of 14.04 LTS, which will be supported until April 2019.

---

### Post by slickymaster on 2015-01-01
Hi sudha2, welcome to the forums.

I've edited your post, adding code tags to it because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of 'Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

Regarding your problem, please have a read at the [Forums Staff recommendations on EOL Ubuntu releases]("http://ubuntuforums.org/showthread.php?t=2229730").

---

