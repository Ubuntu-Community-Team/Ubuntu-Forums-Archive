---
title: "problems upgrading from 8.04 server"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by Nick_Harvey on 2014-03-02
I am following the instructions, but am getting the following error of loads of items not found. What should I do please? fix-missing brings more 404's....
Thanks

```
root@host3:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libneon27 libio-zlib-perl irb1.8 libsasl2 dovecot-common awstats rdoc ri
  subversion libversion-perl libsvn1 spamc libapache2-mod-fcgid
  procmail-wrapper mailman scponly libpg-perl dovecot-imapd irb libapache2-svn
  rdoc1.8 liberror-perl webalizer libgeoip1 libsocket6-perl libdbd-pg-perl
  proftpd dovecot-pop3d python-support libnetaddr-ip-perl libmail-spf-perl
  libreadline-ruby1.8 clamav-daemon libsys-hostname-long-perl
  libarchive-tar-perl ri1.8 spamassassin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1
  libc6-i386
Suggested packages:
  libasound2-plugins
Recommended packages:
  lib32nss-mdns
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1
  libc6-i386
0 upgraded, 7 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 27.3MB of archives.
After this operation, 116MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6-i386 lib32asound2 lib32z1 lib32gcc1 lib32ncurses5 lib32stdc++6
  ia32-libs
Install these packages without verification [y/N]? y
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy/main lib32asound2 1.0.15-3ubuntu4
  404 Not Found [IP: 81.21.76.27 80]
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy/main lib32z1 1:1.2.3.3.dfsg-7ubuntu1
  404 Not Found [IP: 81.21.76.27 80]
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy-updates/main lib32gcc1 1:4.2.4-1ubuntu4
  404 Not Found [IP: 81.21.76.27 80]
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy/main lib32ncurses5 5.6+20071124-1ubuntu2
  404 Not Found [IP: 81.21.76.27 80]
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy-updates/main lib32stdc++6 4.2.4-1ubuntu4
  404 Not Found [IP: 81.21.76.27 80]
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy-security/main libc6-i386 2.7-10ubuntu8.3
  404 Not Found [IP: 81.21.76.27 80]
Err [http://mirrors.webfusion.com](http://mirrors.webfusion.com) hardy-security/universe ia32-libs 2.2ubuntu11.3
  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/main/g/glibc/libc6-i386_2.7-10ubuntu8.3_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/main/g/glibc/libc6-i386_2.7-10ubuntu8.3_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.15-3ubuntu4_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/main/a/alsa-lib/lib32asound2_1.0.15-3ubuntu4_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/main/z/zlib/lib32z1_1.2.3.3.dfsg-7ubuntu1_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/main/z/zlib/lib32z1_1.2.3.3.dfsg-7ubuntu1_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/main/g/gcc-4.2/lib32gcc1_4.2.4-1ubuntu4_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/main/g/gcc-4.2/lib32gcc1_4.2.4-1ubuntu4_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/main/n/ncurses/lib32ncurses5_5.6+20071124-1ubuntu2_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/main/n/ncurses/lib32ncurses5_5.6+20071124-1ubuntu2_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/main/g/gcc-4.2/lib32stdc++6_4.2.4-1ubuntu4_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/main/g/gcc-4.2/lib32stdc++6_4.2.4-1ubuntu4_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
Failed to fetch [http://mirrors.webfusion.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu11.3_amd64.deb](http://mirrors.webfusion.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu11.3_amd64.deb)  404 Not Found [IP: 81.21.76.27 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by sudodus on 2014-03-02
Welcome to the Ubuntu Forums :-)

Your problems could be due to the old age of Ubuntu Server 8.04 LTS. Even though it had long time support, it was limited to 5 years from April 2008, so end of life was April 2013, almost one year ago, and the repositories for updating and upgrading may not be available now.

I don't know enough to help you find what you need, but there are many people (volunteers) at the Ubuntu Forums, who know a lot about Ubuntu Server and about updating and upgrading problems ... with a little bit of luck someone who can help you will read your thread. If no response within 24 hours, you can bump the thread (write 'bump' in a new post).

---

### Post by mörgæs on 2014-03-02
If you want to try the upgrade path here are some instructions:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Still I would suggest a backup and a fresh install of 12.04.

---

