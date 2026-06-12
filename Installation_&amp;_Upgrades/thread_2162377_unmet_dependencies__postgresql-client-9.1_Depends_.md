---
title: "unmet dependencies:  postgresql-client-9.1: Depends: zlib1g (&gt;= 1:1.2.3.3.dfsg) but"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by ni c on 2013-07-14
I'm new to Ubuntu. I've tried solutions suggested in other posts, but none have worked. Tried moving all the postgresql folders out of /usr/share/doc but that did not help.

When I use Package Manager to 'Install all updates' I get this message:

```
The following packages have unmet dependencies:

postgresql-client-9.1: Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                       Depends: postgresql-client-common (>= 115~) but 140~precise is installed
postgresql-contrib-9.1: Depends: postgresql-9.1 (= 9.1.9-0ubuntu12.04) but 9.1.6-1~precise2 is installed
                        Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                        Depends: postgresql-common (>= 115~) but 140~precise is installed

```

It says:

> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f



On running apt-get install -f this is the result:

```
nic@nchvgna29gp:~$ sudo apt-get -f install
[sudo] password for nic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  postgresql-9.1 postgresql-contrib-9.1
Suggested packages:
  oidentd ident-server locales-all libdbd-pg-perl
The following packages will be upgraded:
  postgresql-9.1 postgresql-contrib-9.1
2 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
4 not fully installed or removed.
Need to get 0 B/4 328 kB of archives.
After this operation, 593 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of postgresql-9.1:
 postgresql-client-9.1 (9.1.9-0ubuntu12.04) breaks postgresql-9.1 (<< 9.1.9-0ubuntu12.04) and is installed.
  Version of postgresql-9.1 to be configured is 9.1.6-1~precise2.
dpkg: error processing postgresql-9.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.9-0ubuntu12.04); however:
  Version of postgresql-9.1 on system is 9.1.6-1~precise2.
dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-9.1; however:
  Package postgresql-9.1 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of postgresql-contrib:
 postgresql-contrib depends on postgresql-contrib-9.1; however:
  Package postgresql-contrib-9.1 is not configured yet.
dpkg: error processing postgresql-contrib (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 postgresql-9.1
 postgresql-contrib-9.1
 postgresql
 postgresql-contrib
E: Sub-process /usr/bin/dpkg returned an error code (1)
nic@nchvgna29gp:~$ 


```

I'm have Ubuntu 12.04 LTS, 32-bit currently installed.

Thanks
Nic

---

### Post by ni c on 2013-07-14
Just found this post [http://ubuntuforums.org/showthread.php?t=2112427&p=12493624#post12493624](http://ubuntuforums.org/showthread.php?t=2112427&p=12493624#post12493624) .

I followed the step 
sudo dpkg --force-all -P mysql-server-5.5

and applied it to all the postgresql installations and then ran

sudo apt-get update && sudo apt-get upgrade

and followed whatever those steps recommended and now I seem to have a clean system.

:D

---

### Post by Jason_Wisdom on 2014-02-26
Thanks yours didn't work but I put in this command and it did

sudo apt-get -f update && sudo apt-get -f upgrade

---

