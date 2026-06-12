---
title: "Java Help"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by mw1coe on 2012-03-27
Hi Guys been trying to get Java installed on my System to run jsyn as I have a project that needs these programs..

After trying to add Java jdk7 I now have the following errors when I use terminal to either upgrade or attempt to add any programs..



Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-jdk7-installer (7u3-0~webupd8~1) ...
Downloading...
--2012-03-27 21:14:51--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 174.76.226.42, 174.76.226.9
Connecting to download.oracle.com (download.oracle.com)|174.76.226.42|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-03-27 21:14:51--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.51.90.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.51.90.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-03-27 21:14:52--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|174.76.226.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 3.52M=0.001s

2012-03-27 21:14:52 (3.52 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-jdk7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-jdk7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any Ideas on how to remove this error please ?

Thanks

Rob..

---

### Post by Flymo on 2012-04-06
> If you want to remove oracle-jdk7-installer, you can simply go to
/var/lib/dpkg/info/
It takes some time to load, and delete all files which starts with oracle-java7***** there was ~6files, then go to Synaptic and simply locate same oracle-jdk and click remove/completly remove.

Found the above (by **Vaidotas**) on the [Bodhi Linux forums]("http://forums.bodhilinux.com/index.php?/topic/4621-removing-oracle-jdk7-installer/page__gopid__44152#entry44152") - there's some more discussion on it there - this worked for me!

hth, Ben

---

