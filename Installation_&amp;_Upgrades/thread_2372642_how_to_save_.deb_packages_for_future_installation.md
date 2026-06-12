---
title: "how to save .deb packages for future installation"
date: 2017-09-27
forum: Installation &amp; Upgrades
---

### Post by asteway on 2017-09-27
I used to believe apt saves .deb packages in /var/cache/apt/archives/ for future re/installation. So I installed a package using apt on Ubuntu server 16.04 LTS and saw the /var/cache/apt/archives dir was being populated as I expected.

```

$ apt install mariadb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libaio1 libcgi-fast-perl libcgi-pm-perl libdbd-mysql-perl libdbi-perl...

Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 mysql-common all 5.7.19-0ubuntu0.16.04.1 [15.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 mariadb-common all 10.0.31-0ubuntu0.16.04.2 [16.0 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libdbi-perl amd64 1.634-1build1 [743 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libmysqlclient20 amd64 5.7.19-0ubuntu0.16.04.1 [809 kB]

$ ll /var/cache/apt/archives/
total 16036
drwxr-xr-x 3 root root    4096 Sep 27 15:57 ./
drwxr-xr-x 3 root root    4096 Sep 27 15:49 ../
-rw-r--r-- 1 root root    6356 Oct 24  2015 libaio1_0.3.110-2_amd64.deb
-rw-r--r-- 1 root root   84350 Oct 13  2016 libdbd-mysql-perl_4.033-1ubuntu0.1_amd64.deb
-rw-r--r-- 1 root root  743276 Dec 17  2015 libdbi-perl_1.634-1build1_amd64.deb
-rw-r--r-- 1 root root   86074 Jan 22  2016 libhtml-parser-perl_3.72-1_amd64.deb
-rw-r--r-- 1 root root   13536 May  3  2008 libhtml-tagset-perl_3.20-2_all.deb
-rw-r--r-- 1 root root  809294 Jul 20 20:03 libmysqlclient20_5.7.19-0ubuntu0.16.04.1_amd64.deb
-rw-r--r-- 1 root root   27194 Dec 17  2015 libterm-readkey-perl_2.33-1build1_amd64.deb
-rw-r--r-- 1 root root   76914 Jan 13  2016 liburi-perl_1.71-1_all.deb
-rw-r----- 1 root root       0 Aug  1 14:18 lock
-rw-r--r-- 1 root root 1177754 Aug  4 04:19 mariadb-client-10.0_10.0.31-0ubuntu0.16.04.2_amd64.deb
-rw-r--r-- 1 root root 4374642 Aug  4 04:19 mariadb-client-core-10.0_10.0.31-0ubuntu0.16.04.2_amd64.deb
-rw-r--r-- 1 root root   16042 Aug  4 04:19 mariadb-common_10.0.31-0ubuntu0.16.04.2_all.deb
-rw-r--r-- 1 root root 4155992 Aug  4 04:19 mariadb-server-10.0_10.0.31-0ubuntu0.16.04.2_amd64.deb
-rw-r--r-- 1 root root 4788682 Aug  4 04:19 mariadb-server-core-10.0_10.0.31-0ubuntu0.16.04.2_amd64.deb
-rw-r--r-- 1 root root   15676 Jul 20 20:03 mysql-common_5.7.19-0ubuntu0.16.04.1_all.deb
drwx------ 2 _apt root    4096 Sep 27 15:57 partial/


```

However, once the installation was done, these .deb files were removed automatically. It appears the cache/apt/archives dir was used as a local cache, as its name implies. So how do I save packages as apt downloads them? in RHEL/CentOS/Fedora I'd enable keepcache=1 in yum.conf and also reference a cache dir. Could there be anything similar in Ubuntu? like anything to enable in apt.conf???

---

### Post by Dennis N on 2017-09-27
> So how do I save packages as apt downloads them? 

apt-get has a download option which will save a .deb file from the ubuntu archives to the current working directory.

```
apt-get downolad <package>
```

(maybe you need sudo with this, but I wouldn't think so.)

ADDED: did a quick test - no sudo needed, and don't use .deb with the package name.

example: retrieve gcolor2.deb

```
dmn@Sydney:~$ apt-get download gcolor2
Get:1 http://mirror.cc.vt.edu/pub2/ubuntu/ trusty/universe gcolor2 amd64 0.4-2.1ubuntu1 [25.4 kB]
Fetched 25.4 kB in 0s (73.9 kB/s)
```

---

### Post by ian-weisser on 2017-09-27
> **asteway said:**
> IHowever, once the installation was done, these .deb files were removed automatically.

**EDIT**: The apt archive is not supposed to be cleared automatically by default...but sometimes may be due to a known bug.
Check your apt settings, and be sure you didn't run 'apt clean' or 'apt autoclean' or similar by habit.

/etc/apt/apt.conf.d/10periodic has an autoclean setting.
/etc/apt/apt.conf.d/20archive  has archive size and age settings.

---

### Post by vasa1 on 2017-09-27
> **ian-weisser said:**
> The apt archive is *not *cleared automatically by default. ...
Please see [https://ubuntuforums.org/showthread.php?t=2319347&p=13468613#post13468613](https://ubuntuforums.org/showthread.php?t=2319347&p=13468613#post13468613) or [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=160743#117](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=160743#117)

---

### Post by ian-weisser on 2017-09-27
> **vasa1 said:**
> Please see [https://ubuntuforums.org/showthread.php?t=2319347&p=13468613#post13468613](https://ubuntuforums.org/showthread.php?t=2319347&p=13468613#post13468613) or [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=160743#117](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=160743#117)

Ah, I stand corrected.
Thank you for the links!

---

### Post by asteway on 2017-09-29
> **Dennis N said:**
> apt-get has a download option which will save a .deb file from the ubuntu archives to the current working directory.


Thanks for the reply, but that doesn't help much as I am looking to download packages as I install them. I have also seen that apt-get download doesn't resolve dependencies as does yumdownloader.

---

### Post by asteway on 2017-09-29
> **ian-weisser said:**
> **EDIT**: The apt archive is not supposed to be cleared automatically by default...but sometimes may be due to a known bug.
Check your apt settings, and be sure you didn't run 'apt clean' or 'apt autoclean' or similar by habit.

/etc/apt/apt.conf.d/10periodic has an autoclean setting.
/etc/apt/apt.conf.d/20archive  has archive size and age settings.

Thanks for the reply,

```

$ cat /etc/apt/apt.conf.d/20archive
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";

$ cat /etc/apt/apt.conf.d/10periodic
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";



```

Finally followed the thread on [https://askubuntu.com/questions/464779/apt-get-how-to-make-it-keep-old-archives-locally-when-upgrading-packages](https://askubuntu.com/questions/464779/apt-get-how-to-make-it-keep-old-archives-locally-when-upgrading-packages) and did

```

$ echo 'APT::Clean-Installed "false";' >> /etc/apt/apt.conf

$ apt-config dump|grep Clean
APT::Clean-Installed "false";

```

And the problem was gone. Thanks very much for the help.

---

