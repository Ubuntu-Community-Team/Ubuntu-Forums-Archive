---
title: "Reinstall the apache2"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2016-11-23
I tried to install the mod-evasiv from [this link]("http://www.techrepublic.com/blog/smb-technologist/secure-your-apache-server-from-ddos-slowloris-and-dns-injection-attacks/"), then the apache2 does NOT work at all, it says:

```

env: apache2ctl: No such file or directory

```

I tried so many commands line to resolve it, but by the end I removed the apache2 then try to reinstall it:

```

# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.22-1ubuntu1.11) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.22-1ubuntu1.11) but it is not going to be installed or
                    apache2-mpm-event (= 2.2.22-1ubuntu1.11) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.22-1ubuntu1.11) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.22-1ubuntu1.11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Then as said to try the command apt-get -f install:

```

Do you want to continue [Y/n]? 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "UTF-8",
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 194092 files and directories currently installed.)
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.22-1ubuntu1.11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-bin_2.2.22-1ubuntu1.11_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/apache2/modules/mod_authnz_ldap.so', which is also in package apache2-bin 2.4.16-4+deb.sury.org~precise+4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking apache2.2-common (from .../apache2.2-common_2.2.22-1ubuntu1.11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-common_2.2.22-1ubuntu1.11_amd64.deb (--unpack):
 trying to overwrite '/usr/share/apache2/default-site/index.html', which is also in package apache2-data 2.4.16-4+deb.sury.org~precise+4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.22-1ubuntu1.11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-mpm-worker_2.2.22-1ubuntu1.11_amd64.deb (--unpack):
 trying to overwrite '/usr/sbin/apache2', which is also in package apache2-bin 2.4.16-4+deb.sury.org~precise+4
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2.2-bin_2.2.22-1ubuntu1.11_amd64.deb
 /var/cache/apt/archives/apache2.2-common_2.2.22-1ubuntu1.11_amd64.deb
 /var/cache/apt/archives/apache2-mpm-worker_2.2.22-1ubuntu1.11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The service is not recognized:

```

# service apache2 status
apache2: unrecognized service

```

My configuration is:

```

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

How can I get back the apache2?

Thanks in advance

---

### Post by nikefalcon on 2016-11-26
Looks like you messed up the packaging system; don't worry it can be fixed quite easily most of the time.
Clear out apt archives, lock, and partial files:
```
sudo rm -r /var/cache/apt/archives 
```
Then update lists...
```
 sudo apt update 
```
 and try uninstalling/reinstalling apache. You might need to edit your apt sources.list file. Have you added any extra repositories or are using the default ones only?

---

### Post by alfirdaous on 2016-11-27
I tried the following command lines:


```



######### apt-get update && apt-get -y upgrade


W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/precise/main/source/Sources  404  Not Found          


W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.








######### apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 60 not upgraded.




######### apt-get install -y apache


Fetched 1576 kB in 0s (2691 kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "UTF-8",
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 194088 files and directories currently installed.)
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.22-1ubuntu1.11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-bin_2.2.22-1ubuntu1.11_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/apache2/modules/mod_authnz_ldap.so', which is also in package apache2-bin 2.4.16-4+deb.sury.org~precise+4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking apache2.2-common (from .../apache2.2-common_2.2.22-1ubuntu1.11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-common_2.2.22-1ubuntu1.11_amd64.deb (--unpack):
 trying to overwrite '/usr/share/apache2/default-site/index.html', which is also in package apache2-data 2.4.16-4+deb.sury.org~precise+4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.22-1ubuntu1.11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2-mpm-worker_2.2.22-1ubuntu1.11_amd64.deb (--unpack):
 trying to overwrite '/usr/sbin/apache2', which is also in package apache2-bin 2.4.16-4+deb.sury.org~precise+4
Selecting previously unselected package apache2.
Unpacking apache2 (from .../apache2_2.2.22-1ubuntu1.11_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2.2-bin_2.2.22-1ubuntu1.11_amd64.deb
 /var/cache/apt/archives/apache2.2-common_2.2.22-1ubuntu1.11_amd64.deb
 /var/cache/apt/archives/apache2-mpm-worker_2.2.22-1ubuntu1.11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


#########service apache2 status
apache2: unrecognized service



```


the sources.list file:


```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise universe
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main


# Webmin:
# deb http://download.webmin.com/download/repository sarge contrib
# deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib

```

---

### Post by SeijiSensei on 2016-11-28
> W: Failed to fetch [http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ondrej/php5/ubuntu/dists/precise/main/source/Sources)  404  Not Found 

Go to /etc/apt/sources.list.d and identify the file from "ondrej" providing PHP.  Disable it by renaming the file to have .disabled or some such on the end.  Run "sudo apt-get update" and try again.

Frankly since 12.04 is only supported through next April, I'd upgrade to a newer release like 16.04 Server and see if that works better for you.

---

### Post by alfirdaous on 2016-11-29
I will take the backup then run these command lines, thanks [[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")

---

