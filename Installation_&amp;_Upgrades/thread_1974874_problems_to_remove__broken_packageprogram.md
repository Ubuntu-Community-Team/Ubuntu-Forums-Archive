---
title: "problems to remove  broken package/program"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by balki2005 on 2012-05-06
hi,

I tried  to  install  java on my  ubuntu desktop and followed  a  gude  from the internet.
but it didn't work. now I would like to remove it  but  without  success:

```
onay@ThunderSpeed:~$ sudo apt-get -m remove  oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oracle-java7-installer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 82.9 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
jonay@ThunderSpeed:~$ man apt-get 
jonay@ThunderSpeed:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-06 22:23:11--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 77.67.28.136, 77.67.28.169
Connecting to download.oracle.com (download.oracle.com)|77.67.28.136|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-05-06 22:23:11--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 92.123.238.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|92.123.238.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-05-06 22:23:11--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|77.67.28.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 35.1M=0s

2012-05-06 22:23:11 (35.1 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonay@ThunderSpeed:~$ 
```

what can I do  to remove this  package ?

thanks in advance !

Balki

---

### Post by zvacet on 2012-05-07
> I tried  to  install  java on my  ubuntu desktop and followed  a  gude  from the internet.
but it didn't work.
If you still want to use it then

```
sudo dpkg --configure -a
```

---

