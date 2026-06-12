---
title: "Ubuntu 10.04 Lucid Update Manager fails to update, now 64 days out of date."
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Sun.Dial on 2010-07-04
Hello,
I am trying to update using Update Manager and I get this message:

Failed to fetch "Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net//ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found"

My system is 64 days out of date now.

I have looked elsewhere for an answer and some others have had similar problems, but I have not found a reason for it happening, nor an answer. I wonder if anyone can help me please. I have been using Ubuntu for several months, can use the Terminal if I have the right commands to issue, but beyond that have limited knowledge of the system.
Thank you
Sun

---

### Post by davidmohammed on 2010-07-04
can you try using a different software source ? 

click the "Download From" drop down on the software sources window
Choose Other...

Choose a software source from another country - e.g. United Kingdom - archive.ubuntu.com

Choose Choose Server

---

### Post by Sun.Dial on 2010-07-04
Thanks, I tried the Swiss server and got the same message unfortunately.
Sun

---

### Post by davidmohammed on 2010-07-04
can you run in a terminal

sudo apt-get update
sudo apt-get upgrade


copy and paste the text displayed here within code-tags (# in the toolbar when you reply)

---

### Post by Sonsum on 2010-07-04
> **Sun.Dial said:**
> Hello,
I am trying to update using Update Manager and I get this message:

Failed to fetch "Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net//ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found"

My system is 64 days out of date now.

I have looked elsewhere for an answer and some others have had similar problems, but I have not found a reason for it happening, nor an answer. I wonder if anyone can help me please. I have been using Ubuntu for several months, can use the Terminal if I have the right commands to issue, but beyond that have limited knowledge of the system.
Thank you
Sun

Oddly enough, this effects me too

---

### Post by Sun.Dial on 2010-07-05
Hello David, thanks for the help, here is the text you asked for:

```

  hope that gives you more of an insight into what is going on.
Regards,
Sun
sudo apt-get update
[sudo] password for bb: 
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release.gpg
Ign [http://ppa.launchpad.net//ppa/ubuntu/](http://ppa.launchpad.net//ppa/ubuntu/)  lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release.gpg
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/)  lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid Release.gpg
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release
Hit [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid/main Translation-en_GB
Hit [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid/restricted Translation-en_GB
Hit [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid/universe Translation-en_GB
Hit [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid/multiverse Translation-en_GB
Get: 1 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates Release.gpg [189B]
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid/main Packages
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main Translation-en_GB
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid/main Packages
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid/main Packages
  404  Not Found
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid/main Packages
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/restricted Translation-en_GB
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/universe Translation-en_GB
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/multiverse Translation-en_GB
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security Release.gpg
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-security/main Translation-en_GB
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-security/restricted Translation-en_GB
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-security/universe Translation-en_GB
Ign [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-security/multiverse Translation-en_GB
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid Release
Get: 2 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates Release [44.7kB]
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security Release
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/main Packages  
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/restricted Packages
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/main Sources 
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/restricted Sources
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/universe Packages
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/universe Sources
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/multiverse Packages
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid/multiverse Sources
Get: 3 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/main Packages [247kB]
Get: 4 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/restricted Packages [3,252B]
Get: 5 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/main Sources [89.8kB]
Get: 6 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/restricted Sources [1,292B]
Get: 7 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/universe Packages [62.5kB]
Get: 8 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/universe Sources [18.8kB]
Get: 9 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/multiverse Packages [3,771B]
Get: 10 [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-updates/multiverse Sources [1,499B]
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/main Packages      
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/restricted Packages
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/main Sources
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/restricted Sources
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/universe Packages
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/universe Sources
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/multiverse Packages
Hit [http://mirror.switch.ch]("http://mirror.switch.ch/")  lucid-security/multiverse Sources
Fetched 473kB in 2s (186kB/s) 
W: Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net//ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)   404  Not Found

E: Some index files failed to download, they have been ignored, or old  ones used instead.


sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer libc-bin libc-dev-bin libc6 libc6-dev libc6-i686
  libgstfarsight0.10-0 python-farsight
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.0MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main libc-bin 2.11.1-0ubuntu7.2 [723kB]
Get: 2 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main libc6 2.11.1-0ubuntu7.2 [3,779kB]
Get: 3 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main libc6-i686 2.11.1-0ubuntu7.2 [1,228kB]
Get: 4 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main libc-dev-bin 2.11.1-0ubuntu7.2 [213kB]
Get: 5 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main libc6-dev 2.11.1-0ubuntu7.2 [4,839kB]
Get: 6 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/multiverse flashplugin-installer 10.1.53.64ubuntu0.10.04.3  [19.9kB]
Get: 7 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main libgstfarsight0.10-0 0.0.17-2ubuntu2 [174kB]
Get: 8 [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/)  lucid-updates/main python-farsight 0.0.17-2ubuntu2 [14.9kB]
Fetched 11.0MB in 10s (1,006kB/s)                                               
Preconfiguring packages ...
(Reading database ... 222192 files and directories currently installed.)
Preparing to replace libc-bin 2.11.1-0ubuntu7.1 (using  .../libc-bin_2.11.1-0ubuntu7.2_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.11.1-0ubuntu7.2) ...

(Reading database ... 222192 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu7.1 (using  .../libc6_2.11.1-0ubuntu7.2_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.11.1-0ubuntu7.2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 222192 files and directories currently installed.)
Preparing to replace libc6-i686 2.11.1-0ubuntu7.1 (using  .../libc6-i686_2.11.1-0ubuntu7.2_i386.deb) ...
Unpacking replacement libc6-i686 ...
Preparing to replace libc-dev-bin 2.11.1-0ubuntu7.1 (using  .../libc-dev-bin_2.11.1-0ubuntu7.2_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.11.1-0ubuntu7.1 (using  .../libc6-dev_2.11.1-0ubuntu7.2_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace flashplugin-installer 10.1.53.64ubuntu0.10.04.1  (using .../flashplugin-installer_10.1.53.64ubuntu0.10.04.3_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace libgstfarsight0.10-0 0.0.17-2ubuntu1 (using  .../libgstfarsight0.10-0_0.0.17-2ubuntu2_i386.deb) ...
Unpacking replacement libgstfarsight0.10-0 ...
Preparing to replace python-farsight 0.0.17-2ubuntu1 (using  .../python-farsight_0.0.17-2ubuntu2_i386.deb) ...
Unpacking replacement python-farsight ...
Processing triggers for man-db ...
Setting up libc6-i686 (2.11.1-0ubuntu7.2) ...

Setting up libc-dev-bin (2.11.1-0ubuntu7.2) ...
Setting up libc6-dev (2.11.1-0ubuntu7.2) ...
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.3) ...
Downloading...
--2010-07-05 17:18:10--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4739416 (4.5M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.53.64.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1%  282K  16s
    50K .......... .......... .......... .......... ..........  2%  759K  11s
   100K .......... .......... .......... .......... ..........  3%  954K  9s
   150K .......... .......... .......... .......... ..........  4%  580K  8s
   200K .......... .......... .......... .......... ..........  5%  279K  10s
   250K .......... .......... .......... .......... ..........  6% 21.6M  8s
   300K .......... .......... .......... .......... ..........  7%  574K  8s
   350K .......... .......... .......... .......... ..........  8%  693K  8s
   400K .......... .......... .......... .......... ..........  9% 1.06M  7s
   450K .......... .......... .......... .......... .......... 10% 1.05M  7s
   500K .......... .......... .......... .......... .......... 11% 1.05M  6s
   550K .......... .......... .......... .......... .......... 12% 1.04M  6s
   600K .......... .......... .......... .......... .......... 14%  856K  6s
   650K .......... .......... .......... .......... .......... 15% 1.05M  6s
   700K .......... .......... .......... .......... .......... 16% 1.06M  5s
   750K .......... .......... .......... .......... .......... 17% 1.01M  5s
   800K .......... .......... .......... .......... .......... 18% 1.07M  5s
   850K .......... .......... .......... .......... .......... 19% 1.03M  5s
   900K .......... .......... .......... .......... .......... 20% 1.01M  5s
   950K .......... .......... .......... .......... .......... 21%  975K  5s
  1000K .......... .......... .......... .......... .......... 22% 1.06M  5s
  1050K .......... .......... .......... .......... .......... 23%  659K  5s
  1100K .......... .......... .......... .......... .......... 24%  649K  5s
  1150K .......... .......... .......... .......... .......... 25% 1.04M  4s
  1200K .......... .......... .......... .......... .......... 27% 1.06M  4s
  1250K .......... .......... .......... .......... .......... 28% 1.06M  4s
  1300K .......... .......... .......... .......... .......... 29% 1.05M  4s
  1350K .......... .......... .......... .......... .......... 30% 1.02M  4s
  1400K .......... .......... .......... .......... .......... 31% 1.05M  4s
  1450K .......... .......... .......... .......... .......... 32% 1.06M  4s
  1500K .......... .......... .......... .......... .......... 33% 1.05M  4s
  1550K .......... .......... .......... .......... .......... 34% 1.05M  4s
  1600K .......... .......... .......... .......... .......... 35% 1.05M  4s
  1650K .......... .......... .......... .......... .......... 36% 1.05M  3s
  1700K .......... .......... .......... .......... .......... 37% 1.05M  3s
  1750K .......... .......... .......... .......... .......... 38% 1.05M  3s
  1800K .......... .......... .......... .......... .......... 39% 1.05M  3s
  1850K .......... .......... .......... .......... .......... 41% 1.03M  3s
  1900K .......... .......... .......... .......... .......... 42% 1.04M  3s
  1950K .......... .......... .......... .......... .......... 43% 1.03M  3s
  2000K .......... .......... .......... .......... .......... 44% 1.08M  3s
  2050K .......... .......... .......... .......... .......... 45% 1.05M  3s
  2100K .......... .......... .......... .......... .......... 46% 1.04M  3s
  2150K .......... .......... .......... .......... .......... 47% 1.05M  3s
  2200K .......... .......... .......... .......... .......... 48% 1.06M  3s
  2250K .......... .......... .......... .......... .......... 49% 1.05M  3s
  2300K .......... .......... .......... .......... .......... 50% 1.05M  3s
  2350K .......... .......... .......... .......... .......... 51% 1020K  2s
  2400K .......... .......... .......... .......... .......... 52% 1.09M  2s
  2450K .......... .......... .......... .......... .......... 54% 1.05M  2s
  2500K .......... .......... .......... .......... .......... 55% 1.05M  2s
  2550K .......... .......... .......... .......... .......... 56% 1.05M  2s
  2600K .......... .......... .......... .......... .......... 57% 1.06M  2s
  2650K .......... .......... .......... .......... .......... 58% 1.05M  2s
  2700K .......... .......... .......... .......... .......... 59%  414K  2s
  2750K .......... .......... .......... .......... .......... 60% 26.5M  2s
  2800K .......... .......... .......... .......... .......... 61% 2.59M  2s
  2850K .......... .......... .......... .......... .......... 62% 1.04M  2s
  2900K .......... .......... .......... .......... .......... 63% 1.05M  2s
  2950K .......... .......... .......... .......... .......... 64% 1.06M  2s
  3000K .......... .......... .......... .......... .......... 65% 1.05M  2s
  3050K .......... .......... .......... .......... .......... 66% 1.05M  2s
  3100K .......... .......... .......... .......... .......... 68% 1.05M  2s
  3150K .......... .......... .......... .......... .......... 69% 1.05M  2s
  3200K .......... .......... .......... .......... .......... 70% 1.06M  1s
  3250K .......... .......... .......... .......... .......... 71% 1.05M  1s
  3300K .......... .......... .......... .......... .......... 72% 1.02M  1s
  3350K .......... .......... .......... .......... .......... 73% 1.05M  1s
  3400K .......... .......... .......... .......... .......... 74% 1.06M  1s
  3450K .......... .......... .......... .......... .......... 75% 1.05M  1s
  3500K .......... .......... .......... .......... .......... 76% 1.05M  1s
  3550K .......... .......... .......... .......... .......... 77% 1.06M  1s
  3600K .......... .......... .......... .......... .......... 78% 1.05M  1s
  3650K .......... .......... .......... .......... .......... 79% 1.05M  1s
  3700K .......... .......... .......... .......... .......... 81% 1.05M  1s
  3750K .......... .......... .......... .......... .......... 82% 1.04M  1s
  3800K .......... .......... .......... .......... .......... 83% 1.04M  1s
  3850K .......... .......... .......... .......... .......... 84% 1.05M  1s
  3900K .......... .......... .......... .......... .......... 85% 1.04M  1s
  3950K .......... .......... .......... .......... .......... 86% 1.06M  1s
  4000K .......... .......... .......... .......... .......... 87% 1.05M  1s
  4050K .......... .......... .......... .......... .......... 88% 1.05M  1s
  4100K .......... .......... .......... .......... .......... 89% 1.05M  0s
  4150K .......... .......... .......... .......... .......... 90% 1.06M  0s
  4200K .......... .......... .......... .......... .......... 91% 1.05M  0s
  4250K .......... .......... .......... .......... .......... 92% 1.05M  0s
  4300K .......... .......... .......... .......... .......... 93% 1.02M  0s
  4350K .......... .......... .......... .......... .......... 95% 1.06M  0s
  4400K .......... .......... .......... .......... .......... 96%  783K  0s
  4450K .......... .......... .......... .......... .......... 97% 1007K  0s
  4500K .......... .......... .......... .......... .......... 98% 1.14M  0s
  4550K .......... .......... .......... .......... .......... 99% 1.05M  0s
  4600K .......... .......... ........                        100%  1023K=4.8s

2010-07-05 17:18:15 (973 KB/s) -  `./adobe-flashplugin_10.1.53.64.orig.tar.gz' saved [4739416/4739416]

Download done.
Flash Plugin installed.

Setting up libgstfarsight0.10-0 (0.0.17-2ubuntu2) ...

Setting up python-farsight (0.0.17-2ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by davidmohammed on 2010-07-05
Hi there,
  two ways to resolve this:

go to your administration - software sources screen and click on your other software tab.

unclick all the lines which start "ppa" or a line that says something like "unknown software source" - click close and reload when prompted.

the other way - 

sudo nano /etc/apt/sources.list

look for any line that starts deb [http://ppa.launchpad.net](http://ppa.launchpad.net)

put a # in front of that line
i.e. line reads #deb [http://ppa.launchpad.net](http://ppa.launchpad.net) ....

save

sudo apt-get update

---

### Post by Sun.Dial on 2010-07-06
David, I used your first method and the error message has now gone and Update manager says the system is up to date.
The lines I unchecked were:
[http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu)
and
[http://ppa.launchpad.net//ppa/ubuntu](http://ppa.launchpad.net//ppa/ubuntu)
Are these no longer viable sources?
Is my system now only partially updated now that these software sources are unavailable?
Thanks for your help.
Sun

---

### Post by davidmohammed on 2010-07-06
I suspect that there are no lucid specific packages within those ppa's.  

If you need updated software then you need to see if anyone else has a ppa that meets your needs.

Other than that, I dont see any problems running with older, non updatable software other than that, if a future software update breaks your older software, naturally the older software will not work.

---

### Post by Sun.Dial on 2010-07-06
David,
Thanks for the tips, I'll wait and see then.
Regards,
Sun

---

### Post by Sonsum on 2010-07-07
> **Sonsum said:**
> Oddly enough, this effects me too

My issue was the fact that I had a duplicate universe repo added to my sources. I didn't think that would be an issue!

---

### Post by selen on 2010-07-08
**Please could someone help me ?  I have already for a one week all of this is written on my screen , what should I do ? **
 
**Boot from (hd0,0)ext3c79581de-ca61-4c8c-99f7-2a357b7ab895**
**Starting up...**
**Loading,please wait...**
**Gave up waiting for root device. Common problems:**
**-Boot args(cat/proc/cmdline)**
**-Check rootdelay=(did the system wait long enought ?)**
**-Check root=(did the system wait the right device?)**
**-Missing modules (cat/proc/modules;ls/dev)**
**Alert!/dev/disk/by-uuid/c79581de-ca61-4c8c-99f7-2a35b7ab895 does not exist. Dropping to a shell !**
**BusyBox v1.10.2(Ubuntu 1:1.10.2-ubuntu7) built-in shell(ash)**
**Enter 'help' for a list of built-in commands.**
**(initramfs)**

---

### Post by davidmohammed on 2010-07-08
please start a new thread with your issue.  Thanks.

---

