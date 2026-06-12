---
title: "Replace default apache version by ppa on ubuntu 12.04 LTS"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by mparchet on 2015-08-23
Hello,

I would like to tried to use the ppa repository Instead of the ubutu default package to try to get the last version of the package with my ubuntu version without an ubuntu complete upgrade.

Since I have tried to install apache 2 throw  ppa with this line on ubuntu 12.04 LTS 64 bit

deb [http://ppa.launchpad.net/ondrej/apache2/ubuntu](http://ppa.launchpad.net/ondrej/apache2/ubuntu) precise main 

I get this error message

```

sudo apt-get install -f apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
           Depends: apache2-data (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
 libapache2-mod-php5 : Depends: apache2-api-20120211
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxerces2-java gir1.2-ubuntuoneui-3.0 libbsd0 apache2-mpm-prefork
  apache2.2-common icedtea-netx-common libxml-commons-resolver1.1-java
  libxml-commons-external-java ttf-sil-gentium-basic libubuntuoneui-3.0-1
  thunderbird-globalmenu libcmis-0.2-0 libreoffice-emailmerge
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2 apache2-bin apache2-data
Suggested packages:
  apache2-doc apache2-suexec-pristine apache2-suexec-custom
The following NEW packages will be installed:
  apache2-bin apache2-data
The following packages will be upgraded:
  apache2
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1'260 kB of archives.
After this operation, 4'720 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208161 files and directories currently installed.)
Unpacking apache2-bin (from .../apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man8/apache2.8.gz', which is also in package apache2.2-common 2.2.22-1ubuntu1.10
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Unpacking apache2-data (from .../apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb (--unpack):
 trying to overwrite '/usr/share/apache2/icons/a.png', which is also in package apache2.2-common 2.2.22-1ubuntu1.10
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Preparing to replace apache2 2.2.22-1ubuntu1.10 (using .../apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb) ...
Unpacking replacement apache2 ...
dpkg: error processing /var/cache/apt/archives/apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/apache2/ask-for-passphrase', which is also in package apache2.2-common 2.2.22-1ubuntu1.10
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb
 /var/cache/apt/archives/apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb
 /var/cache/apt/archives/apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ sudo apt-get install -f apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
           Depends: apache2-data (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
 libapache2-mod-php5 : Depends: apache2-api-20120211
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ sudo apt-get install -f apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
           Depends: apache2-data (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
 libapache2-mod-php5 : Depends: apache2-api-20120211
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ clear

mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ sudo apt-get install -f apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
           Depends: apache2-data (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
 libapache2-mod-php5 : Depends: apache2-api-20120211
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ sudo apt-get install -f apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
           Depends: apache2-data (= 2.4.16-3+deb.sury.org~precise+1) but it is not going to be installed
 libapache2-mod-php5 : Depends: apache2-api-20120211
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mparchet@mparchet-W240EU-W250EUQ-W270EUQ:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxerces2-java gir1.2-ubuntuoneui-3.0 libbsd0 apache2-mpm-prefork apache2.2-common icedtea-netx-common
  libxml-commons-resolver1.1-java libxml-commons-external-java ttf-sil-gentium-basic libubuntuoneui-3.0-1 thunderbird-globalmenu
  libcmis-0.2-0 libreoffice-emailmerge
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2 apache2-bin apache2-data
Suggested packages:
  apache2-doc apache2-suexec-pristine apache2-suexec-custom
The following NEW packages will be installed:
  apache2-bin apache2-data
The following packages will be upgraded:
  apache2
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1'260 kB of archives.
After this operation, 4'720 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208161 files and directories currently installed.)
Unpacking apache2-bin (from .../apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man8/apache2.8.gz', which is also in package apache2.2-common 2.2.22-1ubuntu1.10
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Unpacking apache2-data (from .../apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb (--unpack):
 trying to overwrite '/usr/share/apache2/icons/a.png', which is also in package apache2.2-common 2.2.22-1ubuntu1.10
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Preparing to replace apache2 2.2.22-1ubuntu1.10 (using .../apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb) ...
Unpacking replacement apache2 ...
dpkg: error processing /var/cache/apt/archives/apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/apache2/ask-for-passphrase', which is also in package apache2.2-common 2.2.22-1ubuntu1.10
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb
 /var/cache/apt/archives/apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb
 /var/cache/apt/archives/apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Could you help me to fix this bug ?


Thanks for your support

Best regards

mparchet

---

### Post by Alex_Burgett on 2015-08-23
Hey,

I fixed the problem by using dpkg and force overwrite.

```

sudo dpkg -i --force-overwrite /var/cache/apt/archives/apache2-bin_2.4.16-3+deb.sury.org~precise+1_amd64.deb
sudo dpkg -i --force-overwrite /var/cache/apt/archives/apache2-data_2.4.16-3+deb.sury.org~precise+1_all.deb
sudo dpkg -i --force-overwrite /var/cache/apt/archives/apache2_2.4.16-3+deb.sury.org~precise+1_amd64.deb

```

I'm not sure if this is a good way to fix it, but it did the job for me.

---

### Post by ian-weisser on 2015-08-23
> **mparchet said:**
> Could you help me to fix this bug ?

It's not a bug. Apt seems to be behaving correctly.

The system is telling you, in great detail, that you are trying to install packages that *conflict* with each other.
I recommend against forcing it. Down that path lies great frustration and a future reinstall.


> **Alex_Burgett said:**
> I fixed the problem by using dpkg and force overwrite.

Every time the overwritten conflicting packages are updated, the error messages should recur.
The overwrites may prevent a clean upgrade to the next version of Ubuntu. So remember to backup and have a LiveUSB handy.

---

