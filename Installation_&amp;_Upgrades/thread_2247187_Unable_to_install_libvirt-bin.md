---
title: "Unable to install libvirt-bin"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by Romu on 2014-10-06
Hi,
Since few days, I'm facing trouble to install libvirt-bin on Ubuntu trusty64. When I run "sudo apt-get install libvirt-bin", I get:

> Do you want to continue? [Y/n] 
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libnss3-nssdb all 2:3.17-0ubuntu0.14.04.1
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libvirt0 amd64 1.2.2-0ubuntu13.1.2
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libvirt-bin amd64 1.2.2-0ubuntu13.1.2
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libnss3-nssdb all 2:3.17-0ubuntu0.14.04.1
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libnss3 amd64 2:3.17-0ubuntu0.14.04.1
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libxenstore3.0 amd64 4.4.0-0ubuntu5.1
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libxen-4.4 amd64 4.4.0-0ubuntu5.1
  404  Not Found [IP: 91.189.88.149 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-nssdb_3.17-0ubuntu0.14.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-nssdb_3.17-0ubuntu0.14.04.1_all.deb)  404  Not Found [IP: 91.189.88.149 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.17-0ubuntu0.14.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3_3.17-0ubuntu0.14.04.1_amd64.deb)  404  Not Found [IP: 91.189.88.149 80]

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libv/libvirt/libvirt0_1.2.2-0ubuntu13.1.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libv/libvirt/libvirt0_1.2.2-0ubuntu13.1.2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xen/libxenstore3.0_4.4.0-0ubuntu5.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xen/libxenstore3.0_4.4.0-0ubuntu5.1_amd64.deb)  404  Not Found [IP: 91.189.88.149 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xen/libxen-4.4_4.4.0-0ubuntu5.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xen/libxen-4.4_4.4.0-0ubuntu5.1_amd64.deb)  404  Not Found [IP: 91.189.88.149 80]

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libv/libvirt/libvirt-bin_1.2.2-0ubuntu13.1.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libv/libvirt/libvirt-bin_1.2.2-0ubuntu13.1.2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Unfortunately, running the same command with "--fix-missing" leads to the same result. Any idea? Thanks.

EDIT : Just forgot to run "apt-get update", stupid me!

---

