---
title: "Updates does not work using adept"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by b-boy on 2008-11-22
Hi guys


I am trying to download and install updates which the update manager (adept) shows as updates available but it fails with the following error
```
APT Error. Context:
    Package download failed, 
    http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.1.1-1ubuntu1.1_i386.deb: 407 Proxy Authentication Required [IP: 172.28.11.133 8080], 
    http://za.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.0.1-4ubuntu5.3_all.deb: 407 Proxy Authentication Required [IP: 172.28.11.134 8080], 
    http://za.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.0.1-4ubuntu5.3_i386.deb: 407 Proxy Authentication Required [IP: 172.28.11.134 8080], 
    http://za.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.0.1-4ubuntu5.3_i386.deb: 407 Proxy Authentication Required [IP: 172.28.11.134 8080], 
    http://security.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.4ubuntu2.2_i386.deb: 407 Proxy Authentication Required [IP: 172.28.11.133 8080], 
    http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: 407 Proxy Authentication Required [IP: 172.28.11.133 8080], ]
```

and the list goes on ....the funny thing is snaptic works fine a can download and install packages with any problems.

I have tried entering the following settings in .bashrc
but it does not work

```
export export ftp_proxy=http://username:password@proxy:8080
export export ftp_proxy=http://username:password@proxy:8080
```

What could the problem be

---

### Post by Partyboi2 on 2008-11-22
Have you tried to open up /etc/apt/apt.conf and add  you proxy settings?
```
 ACQUIRE::http::Proxy "<YOUR PROXY>";
```

---

### Post by Skripka on 2008-11-22
Adept is in a pretty broken state as of now--I use Synaptic almost exclusively, until they refix Adept.

---

