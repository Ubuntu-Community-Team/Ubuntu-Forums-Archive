---
title: "problem installing Nginx"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by sajil2 on 2015-04-29
hi there i am tring to install Nginx on ubuntu i get error below.using ubuntu 13.10.help please


  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/universe nginx all 1.4.1-3ubuntu1.3
  404  Not Found [IP: 2001:67c:1562::15 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.28-2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.28-2_amd64.deb)  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/n/nginx/nginx-common_1.4.1-3ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/nginx/nginx-common_1.4.1-3ubuntu1.3_all.deb)  404  Not Found [IP: 2001:67c:1562::15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/n/nginx/nginx-full_1.4.1-3ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/nginx/nginx-full_1.4.1-3ubuntu1.3_amd64.deb)  404  Not Found [IP: 2001:67c:1562::15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/n/nginx/nginx_1.4.1-3ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/nginx/nginx_1.4.1-3ubuntu1.3_all.deb)  404  Not Found [IP: 2001:67c:1562::15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by howefield on 2015-04-29
Saucy is end of life as is the repository that you are trying to download from, either point your software sources to old-releases or (preferably) update to a supported release.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by sajil2 on 2015-04-29
you mean update ubuntu or apt-get update?

---

