---
title: "error al actualizar mi 12.04 server de repositorio local"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by frankernesto on 2012-10-23
buena tengo el siguiente problema, instale un repositorio local que descarge de internet con apt-mirror el cual ya esta publicado con el apache en /var/www tengo instalado el entorno de virtualizacion proxmox el el cual cre una maquina virtual openvz de ubuntu 12.04 ya configure el archivo /etc/apt/sources.list con la ip de mi mirror 
deb [http://172.16.1.237/ubuntu/](http://172.16.1.237/ubuntu/) precise main restricted universe multiverse
deb [http://172.16.1.237/ubuntu/](http://172.16.1.237/ubuntu/) precise-update main restricted universe multiverse
deb [http://172.16.1.237/ubuntu/](http://172.16.1.237/ubuntu/) precise-security main restricted universe multiverse

Ahora cuando doy apt-get update me da los siguientes errores y warning 

Err [http://172.16.1.237](http://172.16.1.237) precise-update/main amd64 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/restricted amd64 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/universe amd64 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/multiverse amd64 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/main i386 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/restricted i386 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/universe i386 Packages
  404  Not Found
Err [http://172.16.1.237](http://172.16.1.237) precise-update/multiverse i386 Packages
  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/restricted/bi](http://172.16.1.237/ubuntu/dists/precise-update/restricted/bi)                                                                                                 nary-amd64/Packages  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/universe/bina](http://172.16.1.237/ubuntu/dists/precise-update/universe/bina)                                                                                                 ry-amd64/Packages  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/multiverse/bi](http://172.16.1.237/ubuntu/dists/precise-update/multiverse/bi)                                                                                                 nary-amd64/Packages  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/main/binary-i](http://172.16.1.237/ubuntu/dists/precise-update/main/binary-i)                                                                                                 386/Packages  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/restricted/bi](http://172.16.1.237/ubuntu/dists/precise-update/restricted/bi)                                                                                                 nary-i386/Packages  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/universe/bina](http://172.16.1.237/ubuntu/dists/precise-update/universe/bina)                                                                                                 ry-i386/Packages  404  Not Found

W: Failed to fetch [http://172.16.1.237/ubuntu/dists/precise-update/multiverse/bi](http://172.16.1.237/ubuntu/dists/precise-update/multiverse/bi)                                                                                                 nary-i386/Packages  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/172.16.1.237_ubuntu_dists_pr                                                                                                 ecise-security_main_binary-i386_Packages  Hash Sum mismatch

---

