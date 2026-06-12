---
title: "Aptitude fails to upgrade libc6"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by Sun_Blood on 2012-10-24
Hello

When I was going to upgrade my distro today I run into a problem. Aptitude can't upgrade the libc6 package and I can't remove it and reinstall because the whole system depends on libc6.

Any suggestions?


```
 aptitude upgrade
Resolving dependencies...
The following packages will be upgraded:
  libc6
The following partially installed packages will be configured:
  libc6-dev
1 packages upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Need to get 0 B/4,653 kB of archives. After unpacking 8,192 B will be used.
Do you want to continue? [Y/n/?]
Preconfiguring packages ...
Selecting previously unselected package libc6.
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.3); however:
  Version of libc6 on system is 2.15-0ubuntu10.2.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev

```

---

### Post by Sun_Blood on 2012-10-26
No possible solutions?

---

### Post by Bashing-om on 2012-10-26
hi ! Sun_Blood; 

have you tried terminal codes:
```
sudo apt-get remove libc6
sudo apt-get remove libc6-dev
sudo apt-get install libc6
sudo apt-get install libc6-dev
```Post back with any errors generated.[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by Sun_Blood on 2012-10-26
> **Bashing-om said:**
> hi ! Sun_Blood; 

have you tried terminal codes:
```
sudo apt-get remove libc6
sudo apt-get remove libc6-dev
sudo apt-get install libc6
sudo apt-get install libc6-dev
```Post back with any errors generated.[INDENT]just try'n to help <== BDQ

[/INDENT]

Thanks for the help. Problem is that the whole Linux system is based on libc6 so it's not possible to try to uninstall.

---

### Post by dino99 on 2012-10-26
sudo rm  /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb

Please post the result of:

cat /etc/apt/sources.list

---

### Post by Sun_Blood on 2012-10-26
> **dino99 said:**
> sudo rm  /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb

Please post the result of:

cat /etc/apt/sources.list


```
cat /etc/apt/sources.list
# 

# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://se.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://se.archive.ubuntu.com/ubuntu/ precise universe
deb http://se.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://se.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

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
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by dino99 on 2012-10-26
so your sources.list is clean. If you try to upgrade to Quantal, then replace each precise by quantal, save then update

sudo gedit /etc/apt/sources

---

### Post by Sun_Blood on 2012-10-26
I was hoping not to upgrade the distro. I would prefer to keep this LTS version.

---

### Post by funicorn on 2012-10-26
sudo apt-get -f install

aptitude has been abandoned by your distribution. If you insist using it, you will get yourself into trouble again, sooner or later. In my case aptitude will remove everything if I `run aptitude -f install`. It's not that my system has serious dependency problem, but aptitude simply is inconsistent with nowadays debian package management.

---

### Post by Sun_Blood on 2012-10-26
Ok I thougt aptitude was the replacement for apt-get. But never mind I can use apt-get.

Now I get this error.

```
apt-get -f install libc6 libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-dev is already the newest version.
libc6-dev set to manually installed.
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,653 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by funicorn on 2012-10-26
what's your current working directory ? Because I see ./usr/lib/x86_64-linx-gnu/..

That's wired. Why '[COLOR=Red].[/COLOR]' is there ?

Maybe i should elaborate,

You are doing a dist-upgrade or there is bug in the released package. Do following
```

dpkg -l libc6 libc6-dev
apt-cache madison libc6 libc6-dev

```

See If the versions don't match and paste the output.

---

### Post by dino99 on 2012-10-26
you need to use**[FONT="Arial "] sudo[/FONT]**

(unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted)

---

### Post by Sun_Blood on 2012-10-26
> **dino99 said:**
> you need to use**[FONT=Arial] sudo[/FONT]**

(unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted)

I am root (sudo -i)

```
root@N***TPC:~# dpkg -i /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--install):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
```

---

### Post by Sun_Blood on 2012-10-26
> **funicorn said:**
> what's your current working directory ? Because I see ./usr/lib/x86_64-linx-gnu/..

That's wired. Why '[COLOR=Red].[/COLOR]' is there ?

Maybe i should elaborate,

You are doing a dist-upgrade or there is bug in the released package. Do following
```

dpkg -l libc6 libc6-dev
apt-cache madison libc6 libc6-dev

```See If the versions don't match and paste the output.

OK here is the output.

```
dpkg -l libc6 libc6-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  libc6                  2.15-0ubuntu10.2       Embedded GNU C Library: Shared libraries
iU  libc6-dev              2.15-0ubuntu10.3       Embedded GNU C Library: Development Libraries and Header Fil
root@NASHTPC:~# apt-cache madison libc6 libc6-dev
     libc6 | 2.15-0ubuntu10.3 | http://se.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     libc6 | 2.15-0ubuntu10.2 | http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     libc6 | 2.15-0ubuntu10 | http://se.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
    eglibc | 2.15-0ubuntu10 | http://se.archive.ubuntu.com/ubuntu/ precise/main Sources
    eglibc | 2.15-0ubuntu10.3 | http://se.archive.ubuntu.com/ubuntu/ precise-updates/main Sources
    eglibc | 2.15-0ubuntu10.2 | http://security.ubuntu.com/ubuntu/ precise-security/main Sources
 libc6-dev | 2.15-0ubuntu10.3 | http://se.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
 libc6-dev | 2.15-0ubuntu10.2 | http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 libc6-dev | 2.15-0ubuntu10 | http://se.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
    eglibc | 2.15-0ubuntu10 | http://se.archive.ubuntu.com/ubuntu/ precise/main Sources
    eglibc | 2.15-0ubuntu10.3 | http://se.archive.ubuntu.com/ubuntu/ precise-updates/main Sources
    eglibc | 2.15-0ubuntu10.2 | http://security.ubuntu.com/ubuntu/ precise-security/main Sources
```


I am also thinking about the . but I don't know why is it there.

---

### Post by dino99 on 2012-10-26
one more try:

sudo rm /var/cache/apt/archives/*

then update and sudo apt-get install -f

---

### Post by Sun_Blood on 2012-10-26
> **dino99 said:**
> one more try:

sudo rm /var/cache/apt/archives/*

then update and sudo apt-get install -f

Sadly still same error.


```
root@NASHTPC:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 4,653 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://se.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 amd64 2.15-0ubuntu10.3 [4,653 kB]
Fetched 4,653 kB in 1s (3,264 kB/s)
Preconfiguring packages ...
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by funicorn on 2012-10-26
OK. You can solve this problem by
1. exit from root. sudo -i is always a very bad custom, very very very very bad.
2. type
```

sudo apt-get install --reinstall libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2

```And do NOT upgrade these two packages again until they are fixed by the upstream.

---

### Post by Sun_Blood on 2012-10-27
> **funicorn said:**
> OK. You can solve this problem by
1. exit from root. sudo -i is always a very bad custom, very very very very bad.
2. type
```

sudo apt-get install --reinstall libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2

```And do NOT upgrade these two packages again until they are fixed by the upstream.

Still gives me error. But I guess this can be solved by adding the -f switch but I want to ask you first if that is good or not. libc6 is not a package that I want to be broken/unstable because then the whole server will go down.

btw why is sudo -i bad? And what should I do instead if I want a root shell for a longer period of time? 
I use sudo for quick commands but sometimes I need to do lots as root and adding sudo to all commands is tiresome. 

```
sudo apt-get install --reinstall libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.2)
 libc6-dev : Depends: libc-dev-bin (= 2.15-0ubuntu10.2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Sun_Blood on 2012-10-27
I got curios and tried the -f switch but still get problems. 

I'm thinking we are looking at this problem wrong. It can't be a package error because everyone that have Ubuntu is using the Libc6 package I think. If it was broken then there should be a lot of information on google. 

```
sudo apt-get -f install libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2 libc-bin=2.15-0ubuntu10.2 libc-dev-bin=2.15-0ubuntu10.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc-dev-bin is already the newest version.
libc-dev-bin set to manually installed.
libc6 is already the newest version.
Suggested packages:
  glibc-doc
The following packages will be DOWNGRADED:
  libc-bin libc6-dev
0 upgraded, 0 newly installed, 2 downgraded, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 4 124 kB of archives.
After this operation, 1 024 B disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main libc6-dev amd64 2.15-0ubuntu10.2 [2 944 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main libc-bin amd64 2.15-0ubuntu10.2 [1 181 kB]
Fetched 4 124 kB in 1s (2 291 kB/s) 
dpkg: warning: downgrading libc-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using .../libc-bin_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.3); however:
  Version of libc6 on system is 2.15-0ubuntu10.2.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.3); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu10.2.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 libc6-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by AlexDudko on 2012-10-27
Are there any packages in your system installed from ppa's or manually? They can cause dependency problems.

---

### Post by funicorn on 2012-10-27
Sorry I forgot to come back earlier. Yes, libc6 is very important and any damage is not acceptable. This is exactly why I suggest you have it installed with or even downgraded to a 'safe' version for insurance.

The new error message is not the same as the original one. It only tells that there are other packages of which a higher version has been installed **but** of which a different( lower, in this case)  version is needed by what you are installing. Hence you cannot just downgrade the target package alone, instead you have to downgrade all in the dependency chain as a bunch, which in your case doesn't involve too many, like 4 packages maybe.

So you may have figured out yourself how to solve this, just type the same command again and add more package names to the end. According to the dpkg error report, you should add *libc6-bin=2.15-0ubuntu10.2 and libc6-dev-bin=2.15-0ubuntu10.2*. Just keep in mind that these packages might need to be upgraded again in future.

Anyway the baseline is, if  you run to even more errors after that 'apt-get' command, hold it and see clearly what the output is, and do not rush to confirm the proceeding.

> **Sun_Blood said:**
> Still gives me error. But I guess this can be solved by adding the -f switch but I want to ask you first if that is good or not. libc6 is not a package that I want to be broken/unstable because then the whole server will go down.

btw why is sudo -i bad? And what should I do instead if I want a root shell for a longer period of time? 
I use sudo for quick commands but sometimes I need to do lots as root and adding sudo to all commands is tiresome. 

```
sudo apt-get install --reinstall libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.2)
 libc6-dev : Depends: libc-dev-bin (= 2.15-0ubuntu10.2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Sun_Blood on 2012-10-29
Hi,

So the problems continues.

```
apt-get install --reinstall libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2 libc-bin=2.15-0ubuntu10.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  glibc-doc
The following packages will be DOWNGRADED:
  libc6-dev
0 upgraded, 0 newly installed, 2 reinstalled, 1 downgraded, 0 to remove and 32 not upgraded.
1 not fully installed or removed.
Need to get 8 776 kB of archives.
After this operation, 1 024 B disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main libc6-dev amd64 2.15-0ubuntu10.2 [2 944 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main libc-bin amd64 2.15-0ubuntu10.2 [1 181 kB]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/main libc6 amd64 2.15-0ubuntu10.2 [4 651 kB]                                                                                                                                       
Fetched 8 776 kB in 18s (469 kB/s)                                                                                                                                                                                                           
Preconfiguring packages ...
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.2 (using .../libc-bin_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_amd64.deb (--unpack):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by funicorn on 2012-10-29
add libc-dev-bin=...

---

### Post by Sun_Blood on 2012-11-01
> **funicorn said:**
> add libc-dev-bin=...

Still same. Very strange this.

```
apt-get install --reinstall libc6=2.15-0ubuntu10.2 libc6-dev=2.15-0ubuntu10.2 libc-bin=2.15-0ubuntu10.2 libc-dev-bin=2.15-0ubuntu10.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  glibc-doc
The following packages will be DOWNGRADED:
  libc6-dev
0 upgraded, 0 newly installed, 3 reinstalled, 1 downgraded, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 84,5 kB/8 860 kB of archives.
After this operation, 1 024 B disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main libc-dev-bin amd64 2.15-0ubuntu10.2 [84,5 kB]
Fetched 84,5 kB in 0s (316 kB/s)        
Preconfiguring packages ...
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.2 (using .../libc-bin_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
(Reading database ... 68879 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_amd64.deb (--unpack):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by funicorn on 2012-11-01
Wired it is. can you check the file permission of [I]`/usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' ?

[/I]In my case it's *-rw-r--r--* with owner:group* root:root*. And
```

ldd /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so

```> 
    linux-vdso.so.1 =>  (0x00007ffffd2f4000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f42ee7b7000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f42eeda7000)
What's also wired is dpkg wants to backup link of `*./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so*.' I just cannot understand why [COLOR=Red][COLOR=Black]`[/COLOR]**.**[COLOR=Black]'[/COLOR][/COLOR] is there. Anyway I think it's related to the link library files of [I]`/usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so'. So check those too.
[/I]

---

### Post by Sun_Blood on 2012-11-02
> **funicorn said:**
> Wired it is. can you check the file permission of [I]`/usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' ?

[/I]In my case it's *-rw-r--r--* with owner:group* root:root*. And
```

ldd /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so

```What's also wired is dpkg wants to backup link of `*./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so*.' I just cannot understand why [COLOR=Red][COLOR=Black]`[/COLOR]**.**[COLOR=Black]'[/COLOR][/COLOR] is there. Anyway I think it's related to the link library files of [I]`/usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so'. So check those too.
[/I]

I hope we can find a solution soon :)
```
root@NA*****:~#ldd /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
        linux-vdso.so.1 =>  (0x00007fff683ff000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f1bd663e000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f1bd6c08000)

root@*****C:~# ls -al /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
-rw-r--r-- 1 root root 10272 Sep 29 11:51 /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
```

---

### Post by funicorn on 2012-11-03
To be honest I coundn't understand what's happening during the libc6 installation. It seems it tries to commit the preinst script in the debian directory inside the package. But I'm totally lost for the specific action of 'make backup link of  `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so'. 

You can try to run the downgrade command under '/' and see what happens.

Also, you can use dpkg --force-downgrade -i xxx.deb to force downgrade debian packages, in which case you need download the wanted version of above packages in advance. However it might bring up risk to damage the system. Use it with caution.

[SIZE=3][COLOR=Red]_Do not force downgrade, see the [SIZE=3][SIZE=3]new[/SIZE] pos[SIZE=3]t[SIZE=3] below.[/SIZE][/SIZE][/SIZE]_
[/COLOR][/SIZE]

---

### Post by funicorn on 2012-11-03
OK I downloaded the libc6 package and looked in to the debian scripts inside. I found the problem occurred to you is related the prerm script, which is used to preserve the system library links. I'm still not clear about the details. But I'm sure it's related to /lib64, which is either a symbol link to /lib or a real directory. This is the key difference. It's possible that a old version of libc6 uses symbol link of /lib64, where as a higher version uses real directory. So you should do following things:

[LIST]
[*]Do not downgrade libc6 with --force-downgrade, since I realized it's very dangerous.
[/LIST]

[LIST]
[*]check the path /lib64 is a symbol link or a real directory
[/LIST]
 
[LIST]
[*]check what reside in /lib64, are they all symbol links or real files
[/LIST]
 
[LIST]
[*]download the debian package of the current version of libc6 installed in your system, open it with file-roller, compare the files in /lib64 of the archive and those in /lib64 of your system, to see if there is any difference.
[/LIST]

[LIST]
[*]you can also download the old version of libc6, open it and compare the files in /lib64 with those in the newer(currently installed) version.
[/LIST]

---

### Post by Tomelirolla on 2012-11-04
I'm having the same problem. When I try to update anything or install anything from software centre I get ```
The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.15-0ubuntu10.2) but 2.15-0ubuntu10.3 is installed
libc6-dev: Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.2 is installed
           Depends: libc-dev-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.3 is installed
libc6-i386: Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.2 is installed
libc6:i386: Depends: libc-bin (= 2.15-0ubuntu10.2) but 2.15-0ubuntu10.3 is installed
``` I tried ```
sudo apt-get -f install
``` and I got ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  amarok-help-en
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 0 newly installed, 0 to remove and 107 not upgraded.
5 not fully installed or removed.
Need to get 0 B/8,593 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 275361 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...

A copy of the C library was found in an unexpected directory:
  '/lib/x86_64-linux-gnu/libc-2.15.so.dpkg-tmp'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/x86_64-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Sun_Blood on 2012-11-04
> **funicorn said:**
> OK I downloaded the libc6 package and looked in to the debian scripts inside. I found the problem occurred to you is related the prerm script, which is used to preserve the system library links. I'm still not clear about the details. But I'm sure it's related to /lib64, which is either a symbol link to /lib or a real directory. This is the key difference. It's possible that a old version of libc6 uses symbol link of /lib64, where as a higher version uses real directory. So you should do following things:

[LIST]
[*]Do not downgrade libc6 with --force-downgrade, since I realized it's very dangerous.
[/LIST]

[LIST]
[*]check the path /lib64 is a symbol link or a real directory
[/LIST]
 
[LIST]
[*]check what reside in /lib64, are they all symbol links or real files
[/LIST]
 
[LIST]
[*]download the debian package of the current version of libc6 installed in your system, open it with file-roller, compare the files in /lib64 of the archive and those in /lib64 of your system, to see if there is any difference.
[/LIST]

[LIST]
[*]you can also download the old version of libc6, open it and compare the files in /lib64 with those in the newer(currently installed) version.
[/LIST]


Hi,
I feel you are on the right track here, but I can't relay understand exactly what I need to do.

I checked /lib64 and it's a real directory but inside that there is 1 file that is only a symbolic link.
```
root@N***C:/# ls -al /
total 96
*****
drwxr-xr-x  21 root root  4096 Oct 16 11:58 lib
drwxr-xr-x   2 root root  4096 Oct  3 06:46 lib64
*****
root@N****C:/# ls -al /lib64/
total 8
drwxr-xr-x  2 root root 4096 Oct  3 06:46 .
drwxr-xr-x 23 root root 4096 Oct 12 06:51 ..
lrwxrwxrwx  1 root root   32 Sep 29 11:51 ld-linux-x86-64.so.2 -> /lib/x86_64-linux-gnu/ld-2.15.so
root@NASHTPC:/# 
```

What should I do as the next step?

---

### Post by funicorn on 2012-11-04
check if there is a file /lib/ld-linux-x86-64.so.2

if NOT, then try 
```
 sudo cp -a /lib64/ld-linux-x86-64.so.2 /lib/
```
and see what happens. 

It's only a test. If nothing happens, delete the newly copied file /lib/ld-linux-x86-64.so.2.

---

### Post by Sun_Blood on 2012-11-05
I didn't do any different sadly.

---

### Post by Sun_Blood on 2012-12-03
Ok I am throwing out the question again to see if anyone have an answer to my problem. Or I will try to set aside some time to reinstall ubuntu this weekend.

Please someone help me to solve this problem. I don't want to lose my faith in Ubuntu and that you don't have to reinstall Linux all the time. :confused::confused:

---

### Post by Sun_Blood on 2012-12-08
> **dino99 said:**
> so your sources.list is clean. If you try to upgrade to Quantal, then replace each precise by quantal, save then update

sudo gedit /etc/apt/sources

FYI I have now even tryed to upgrade to Quantal but still get the exact same problem.

```
Preconfiguring packages ...
(Reading database ... 68881 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu20_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu20_amd64.deb (--unpack):
 unable to make backup link of `./usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu20_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Sun_Blood on 2012-12-08
Just for fun I try to move the file. but I cant... 
Is it possible this have something to do with permissions or is the file locked by the system?

```
root@N****C:~# mv /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so .                                                 
mv: cannot move `/usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so' to `./ISO8859-10.so': Operation not permitted

root@N****C:~# ls -al /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
-rw-r--r-- 1 root root 10272 Sep 29 11:51 /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
```

---

### Post by Sun_Blood on 2012-12-08
Solved!!

It was a problems with permissions. For some reason all the chattr flags was activated for this file and normally only e is active.

Now the upgrade didn't have any problems and the apt-get upgrade was successful.

---

### Post by bfcrowrench on 2012-12-16
Sun_Blood, can you please elaborate on your solution?  I am having the same problem and I'm very eager to fix it.

Thanks!

---

### Post by Sun_Blood on 2012-12-16
> **bfcrowrench said:**
> Sun_Blood, can you please elaborate on your solution?  I am having the same problem and I'm very eager to fix it.

Thanks!

Sure.

The problem was that the file had got a protected file attribute flag activated for some reason. After removing that the system could update the file.

If you run the command lsattr the output should looks same as below.
```
norty@N****C:~$ lsattr /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so 
-------------e-- /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
```

If you for some reason have more flags then --------e-- then you have a problem.
To fix it can use the command chattr.

```

chattr -AaCcDdijsSu  /usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so 
```

And then just do the command apt-get upgrade.
Or if you like me have played around with downgrades try apt-get -f upgrade

---

### Post by bfcrowrench on 2012-12-16
Well, shoot...

```
raoulduke@ubuntu /u/l/x/gconv> lsattr ISO8859-10.so 
-------------e- ISO8859-10.so

```

Looks like that wasn't my problem.  

Honestly, I don't know what ISO8859-10.so is or how it relates to this issue.   So maybe I need to check the flags set on other files too?   Any suggestions?

My only other idea is to go through the thread and try the solutions that didn't work for you.   I didn't start there, I started with your solution.

By the way, thank you for your response with the details of your solution.   I was so optimistic that it would solve my problem!

---

### Post by bfcrowrench on 2012-12-16
Ok, as I look through the previous suggestions I'm seeing how the ISO file emerged in an error message from some troubleshooting.

I'll work with those earlier steps and I'll update with the outcome.

Thanks!

---

### Post by bfcrowrench on 2012-12-28
Hello again!  I found some time to revisit this issue.

After reviewing the thread, I see where that the *ISO8859-10.so* file that we discussed emerged when you ran *sudo apt-get -f install*.

Unfortunately, I don't have that (or any filename) appearing in my error response from apt-get.   I'll show you what I'm getting:

```
raoulduke@ubuntu ~> sudo apt-get -f install
[sudo] password for raoulduke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-26-generic libkipi8 libdiscid0 libkwinactiveeffects1abi3 linux-headers-3.2.0-24 linux-headers-3.2.0-26 linux-headers-3.2.0-29 libglew1.5
  linux-headers-3.2.0-29-generic libkwineffects1abi3 linux-headers-3.2.0-24-generic libnepomukdatamanagement4 kdegraphics-mobipocket libkexiv2-10 libmusicbrainz3-6
  libkwinactiveglutils1 libkwinglutils1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libc6-i386
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6-dev libc6-i386
2 upgraded, 0 newly installed, 0 to remove and 230 not upgraded.
2 not fully installed or removed.
Need to get 0 B/6,938 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 libc6-dev
 libc6-i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions are welcome!

Thanks!

~b

---

