---
title: "apt-get upadte fails"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by bmagill on 2006-06-04
OK, this is my second attempt to get some help with this issue.  I have done my best to research it.  I cannot figure out what the problem is.

When I attempt to update the repositories and install software, I am getting errors.  Everything worked fine in Breezy.  This is a post update to Dapper issue.  I updated using the update manager.

Please help.  Perhaps I need to submit a bug report?  Why is it trying to connect to localhost?


```
user@host:/var/lib/apt/lists$ sudo apt-get update
Password:
Err http://wine.sourceforge.net binary/ Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://cran.R-project.org stable/ Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://packages.freecontrib.org breezy Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 C onnection refused)
Failed to fetch http://wine.sourceforge.net/apt/binary/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused )
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connecti on refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (11 1 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 C onnection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 C onnection refused)
Failed to fetch http://cran.R-project.org/bin/linux/debian/stable/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connect ion refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
brett@freud:/var/lib/apt/lists$ sudo apt-get update
Err http://packages.freecontrib.org breezy Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://cran.R-project.org stable/ Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://wine.sourceforge.net binary/ Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://wine.sourceforge.net/apt/binary/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://cran.R-project.org/bin/linux/debian/stable/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by ubuntu_demon on 2006-06-04
> 
During dist-upgrading from Breezy to Dapper non-official repos should be commented. Dist-upgrading using the update-manager tool is easy as it comments all non-official repo's automatically.


Please go here :

warning / take a look here prior to upgrading and installing :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]Please go here :

warning / take a look here prior to upgrading and installing :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)[/QUOTE]


OK, I went there.  In fact, I read that before I updated, particulary this line:

> During dist-upgrading from Breezy to Dapper non-official repos should be commented. Dist-upgrading using the update-manager tool is easy as it comments all non-official repo's automatically.

Like I said, I updated with the update-manager.  Then, I reactivated additional archives post-dist-upgrade to update my other software.

Thanks, but I don't think that is the problem.

Brett

---

### Post by ubuntu_demon on 2006-06-04
Please post your /etc/apt/sources.list

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]Please post your /etc/apt/sources.list[/QUOTE]

This the the post-upgrade sources list.  I reactivated several after dist-upgrading with update-manager, which, as you said, commented out all but the main repositories.

Also, isn't this line in the error message telling?  Why is it http'ing to local host.  I have no server running! Of course the connection is refused.

> Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)


```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb http://wine.sourceforge.net/apt/ binary/
# deb http://deb.opera.com/opera etch non-free
# The above lines were generated automatically by EasyUbuntu.
# The rest of your sources.list follows

deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## More backports
# deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free
## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
# deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
# deb http://people.ubuntu.com/~doko/OOo2 ./

## R Debian Repository on CRAN
deb http://cran.R-project.org/bin/linux/debian stable/
```

---

### Post by ubuntu_demon on 2006-06-04
you made some mistakes. Use a clean Dapper sources.list from here :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

**WARNING / take a look here prior to upgrading and installing!**
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]you made some mistakes. Use a clean Dapper sources.list from here :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

**WARNING / take a look here prior to upgrading and installing!**
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)[/QUOTE]

WHAT MISTAKES?  I may well have done something wrong, but nothing in that doc suggests it.  Thanks.
I did read several docs in these forums, including that one before upgrading and I used the update manager to do my upgrade.

Problems with the sources.list it was an interesting theory, but incorrect in the face of the evidence.  Despite the fact that I did not think you were right, I changed my sources list to the clean versions.  It is still not working, same error.  

Can someone who knows something about apt-get tell me why it is looking for repositories on localhost and not going out to the network?  Particuarly note the line:

```
Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
```

Here is my sources,list, after changing it and cutting out any extras:

```
user@network:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

And here are the same errors.

```
brett@freud:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by rcarring on 2006-06-04
Do 

```

ifconfig

```

and post the results here. I don't think your network connection is working as expected.

Probably dns is fouled up.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=bmagill]WHAT MISTAKES?  I may well have done something wrong, but nothing in that doc suggests it.  Thanks.
I did read several docs in these forums, including that one before upgrading and I used the update manager to do my upgrade.

Problems with the sources.list it was an interesting theory, but incorrect in the face of the evidence.  Despite the fact that I did not think you were right, I changed my sources list to the clean versions.  It is still not working, same error.  

Can someone who knows something about apt-get tell me why it is looking for repositories on localhost and not going out to the network?  Particuarly note the line:

```
Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
```

Here is my sources,list, after changing it and cutting out any extras:

```

user@network:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

And here are the same errors.

```

brett@freud:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```
[/QUOTE]

I understand that you have dist-upgraded using the update-manager but I advice to keep non-official repositories commented or keep using the clean sources.list until you have solved all your problems. Having this repo enabled was a mistake :
> 
## R Debian Repository on CRAN
deb [http://cran.R-project.org/bin/linux/debian](http://cran.R-project.org/bin/linux/debian) stable/


I first wanted to make sure the problem is not directly related to typos in the sources.list and that your sources.list is clean and in order.

Post your /etc/resolv.conf and make sure those nameservers are correct (find them using the homepage of your provider) :
$cat /etc/resolv.conf

Post the results of route :
$route

Post the results of ifconfig (as suggested by rcarring) :
$ifconfig

Post the result of :
$cat /etc/network/interfaces

I want to know the contents of :
$cat /etc/hosts
$cat /etc/hostname

Make sure the permissions of /etc/apt/sources.list and /etc/apt/apt.conf are allright see :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

I want to know wether apt-get wants to remove anything due to broken dependencies :
$sudo apt-get remove -f

I want to know if you have installed ubuntu-base and ubuntu-desktop :
$dpkg -l | grep ubuntu-base
$dpkg -l | grep ubuntu-desktop

(ubuntu-desktop is not related to the apt problem but it useful to make sure it is installed correctly)

don't worry we'll probably solve it if you have enough patience :D

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]I understand that you have dist-upgraded using the update-manager but I advice to keep non-official repositories commented or keep using the clean sources.list until you have solved all your problems. You had this repository enabled :

We'll just have to tackle things one at a time. [/QUOTE]

Thank you.  here is the information in reply to the previosu two posts:

Networking is apparently working.  I am posting from this machine.  Internet OK, so far as I can see.  DNS is asigned by DHCP and everything appears happy.

resolv.conf contains

```
cat /etc/resolv.conf
search psyche.home
nameserver 68.94.156.1
nameserver 68.94.157.1 
```

```

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:2C:05:71:2F
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:2cff:fe05:712f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:49873734 (47.5 MiB)  TX bytes:8703172 (8.2 MiB)
          Interrupt:185 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:634520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:634520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:107480524 (102.5 MiB)  TX bytes:107480524 (102.5 MiB)

```

```

 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```
```

cat /etc/hosts
127.0.0.1 localhost.localdomain localhost freud

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/hostname
freud

```

```

sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

```

user@freud:~$ dpkg -l | grep ubuntu-base
ii  ubuntu-base                            0.119                                    The Ubuntu base system (transitional package
user@freud:~$ dpkg -l | grep ubuntu-desktop
ii  ubuntu-desktop                         0.119                                    The Ubuntu desktop system

```

```

ls -al /etc/apt/sources.list
-rw-r--r-- 1 root root 1792 2006-06-04 10:38 /etc/apt/sources.list

ls -al /etc/apt/apt.conf
-rw-r--r-- 1 root root 0 2006-06-03 15:27 /etc/apt/apt.conf

```

But note, apt.conf is empty??  Is is supposed to be?

---

### Post by ubuntu_demon on 2006-06-04
AFAIK there's no problem with an apt.conf being empty. So this is probably not the solution we are seeking. But I don't know the meaning of the second line in my apt.conf. So you should try to make it like mine. It can't hurt and there is a very small chance that we get lucky :)

You may try to add these lines to /etc/apt/apt.conf

> 
APT::Authentication::TrustCDROM "true";
Acquire::::Proxy "false";


My desktop computer is also getting it's IP and stuff from my gateway. Here's another small difference. It can't hurt to try. But it's only a very small chance that this is the solution.

Make your /etc/hosts like mine :

```

127.0.0.1 localhost *myhostname*
127.0.1.1 *myhostname*

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$sudo apt-get update

It very likely won't help. But it can't hurt to try. 

Also please check the permissions of all the files mentioned using :
$ls -al *filename*

And I want to know the result of :
$uname -a

I'll think a bit more about your problem. But now I'm going offline for a while .. maybe several hours.

good luck! :)

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=bmagill]
```

sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
[/QUOTE]

$sudo apt-get dist-upgrade

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]$sudo apt-get dist-upgrade[/QUOTE]

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gdk-imlib1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Changes to hosts file and apt.conf made

```

uname -a
Linux freud 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

Results the same, cannot connect to localhost

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=bmagill]sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gdk-imlib1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/QUOTE]

Try and see which of these two options you like :

This will upgrade gdk-imlib1 but some package(s) may need to be removed :
$sudo apt-get install gdk-imlib1
This will remove gdk-imlib1 but some other package(s) may need to be removed :
$sudo apt-get remove gdk-imlib1


[QUOTE=bmagill]
Changes to hosts file and apt.conf made

```

uname -a
Linux freud 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

```

Results the same, cannot connect to localhost[/QUOTE]

I thought so :(.

First try a reboot and then try again :
$sudo apt-get update

Then try pinging the servers which give you problems and also ping localhost. Report the errors.

Please post also this information :
[http://www.ubuntuforums.org/showpost.php?p=1092144&postcount=32](http://www.ubuntuforums.org/showpost.php?p=1092144&postcount=32)
[http://www.ubuntuforums.org/showpost.php?p=1092194&postcount=35](http://www.ubuntuforums.org/showpost.php?p=1092194&postcount=35)

You might try a k7 or 686 kernel depending on which processor you have. It probably won't be a solution but it can't hurt to exclude it :
$sudo apt-get install linux-k7  
or :
$sudo apt-get install linux-686
reboot and try again.

I'll check back in a couple of hours.

good luck!

---

### Post by khedron on 2006-06-04
Okay, my error was not about a connection to localhost, but to the external sites i.e. security.ubuntu.com etc.

The way I solved this was to visit security.ubuntu.com in firefox. After this, apt-get update worked. Maybe something to do with DNS?

---

### Post by bmagill on 2006-06-04
[QUOTE=khedron]Okay, my error was not about a connection to localhost, but to the external sites i.e. security.ubuntu.com etc.

The way I solved this was to visit security.ubuntu.com in firefox. After this, apt-get update worked. Maybe something to do with DNS?[/QUOTE]


The real question is, why is it trying to connect to localhost at all???  No runnung server, no reason to look there.

---

### Post by llamakc on 2006-06-04
You may have answered this but do you have a proxy configured (or used to have one)?

What about an old proxy line in .bashrc?

How about doing ctrl-alt-f1 to a terminal TTY and logging in as root and trying it from there?

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=bmagill]The real question is, why is it trying to connect to localhost at all???  No runnung server, no reason to look there.[/QUOTE]
It can't hurt to try his suggestion.

Also do you have some kind of firewall installed ?

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]You may have answered this but do you have a proxy configured (or used to have one)?

What about an old proxy line in .bashrc?

How about doing ctrl-alt-f1 to a terminal TTY and logging in as root and trying it from there?[/QUOTE]


No, never.  Does the upgrade process make use of a proxy server?  Residuals left over?

---

### Post by llamakc on 2006-06-04
What's the output of `dpkg -l | grep proxy` and the router you're connecting to: what type is it?

---

### Post by llamakc on 2006-06-04
May we also see what processes are chugging away on your box?

`ps aux`

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]What's the output of `dpkg -l | grep proxy` and the router you're connecting to: what type is it?[/QUOTE]

```

 dpkg -l | grep proxy
ii  python-egenix-mxproxy                  2.0.6ubuntu1-1ubuntu4                    generic proxy wrapper type for Python [dummy
ii  python2.4-egenix-mxproxy               2.0.6ubuntu1-1ubuntu4                    generic proxy wrapper type for Python 2.4
ii  smproxy                                1.0.1-0ubuntu1                           X client - smproxy

```

My router is a linksys, no problems with Breezy

---

### Post by llamakc on 2006-06-04
I have the same entries. How about processes running?

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]I have the same entries. How about processes running?[/QUOTE]


Not inclined to show all running processes, especially with as much networing info as I have posted, but what about this:

```

privoxy  23407  0.0  0.1   2288   944 ?        SNs  07:35   0:00 /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config

```

Perhaps I should try to kill it.  Anything else i should look for?

---

### Post by llamakc on 2006-06-04
ken@vulva:~$ ps aux | grep privoxy
ken      32427  0.0  0.0   2880   800 pts/0    S+   15:18   0:00 grep privoxy


It's not running on my box. I'd kill it and give a try with apt-get again.

---

### Post by ubuntu_demon on 2006-06-04
privoxy and/or tor is probably the problem. This explains all symptoms :).

$sudo apt-get remove tor privoxy --purge

These packages are recommended/suggested by tor. If you have them installed you could also try to remove them :privoxy, socat mixmaster, mixminion, anon-proxy

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]privoxy and/or tor is probably the problem. This explains all symptoms :).

$sudo apt-get remove tor privoxy --purge

These packages are recommended/suggested by tor. If you have them installed you could also try to remove them :privoxy, socat mixmaster, mixminion, anon-proxy[/QUOTE]

Alas, privoxy is gone and none of the other packages installed.  Synaptic still wants to connect to localhost!?!

---

### Post by llamakc on 2006-06-04
/etc/init.d/networking restart

---

### Post by llamakc on 2006-06-04
And logout as that user and log back in.

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]/etc/init.d/networking restart[/QUOTE]

```

 sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:50:2c:05:71:2f
Sending on   LPF/eth0/00:50:2c:05:71:2f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 42892 seconds.
                                                                         [ ok ]

```

```

http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

```

Arghhhh...!

---

### Post by ubuntu_demon on 2006-06-04
Try a reboot and try again.

If it doesn't work : I want to know which packages have leftover configuration files :

I hope you have installed deborphan or manage to install it :
$sudo apt-get install deborphan 
$deborphan --find-config

Now let's see what else is installed on your system :

You can also post :
$dpkg -l
$dpkg -l > packagelist.txt

Or if that list is too big. Here's how to create shorter list.
> 
 debfoster maintains a list of installed packages that were explicitly requested rather than installed as a dependency. 

$sudo apt-get install debfoster
$sudo debfoster -q
$cat /var/lib/debfoster/keepers

You don't have to report packages that start with : lib

---

### Post by bmagill on 2006-06-04
[QUOTE=ubuntu_demon]Try a reboot and try again.

If it doesn't work : I want to know which packages have leftover configuration files :

I hope you have installed deborphan or manage to install it :
$sudo apt-get install deborphan 
$deborphan --find-config

Now let's see what else is installed on your system :

You can also post :
$dpkg -l
$dpkg -l > packagelist.txt

Or if that list is too big. Here's how to create shorter list.

$sudo apt-get install debfoster
$sudo debfoster -q
$cat /var/lib/debfoster/keepers

You don't have to report packages that start with : lib[/QUOTE]


I don't have either of these installed and in its current state, apt-get is uncooperative.  Can I download the .debs?

---

### Post by llamakc on 2006-06-04
Let's see the output of `env`

Did you ever get around to logging out and back in? Or trying as a pure root user?

sudo passwd root

and then 

su -

and run apt-get update && apt-get dist-upgrade

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]Let's see the output of `env`

Did you ever get around to logging out and back in? Or trying as a pure root user?

sudo passwd root

and then 

su -

and run apt-get update && apt-get dist-upgrade[/QUOTE]

Ye, I logged out and back in, tried it.  Rebooted, tried it.  No go.

No luck as root, same errors.

Here is env:

```

 env
SSH_AGENT_PID=4968
TERM=xterm
DESKTOP_STARTUP_ID=
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/brett/.gtkrc-1.2-gnome2
WINDOWID=33554525
http_proxy=http://localhost:8080/
USER=brett
GNOME_KEYRING_SOCKET=/tmp/keyring-px54sT/socket
SSH_AUTH_SOCK=/tmp/ssh-DTWbFo4922/agent.4922
SESSION_MANAGER=local/freud:/tmp/.ICE-unix/4922
USERNAME=brett
DESKTOP_SESSION=default
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/brett
LANG=en_US.UTF-8
GDMSESSION=default
HOME=/home/brett
SHLVL=1
LANGUAGE=en
no_proxy=localhost,127.0.0.0/8,*.local
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=brett
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-hr7ukNHiJb,guid=278883448cf71b6a3d9f7a32dfac7100
DISPLAY=:0.0
COLORTERM=gnome-terminal
XAUTHORITY=/home/brett/.Xauthority
_=/usr/bin/env

```

---

### Post by llamakc on 2006-06-04
http_proxy=http://localhost:8080/

Right there is your problem. That's why I wanted to see your .bashrc. Perhaps privoxy|tors left something in /etc? That's why it won't connect.

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]http_proxy=http://localhost:8080/

Right there is your problem. That's why I wanted to see your .bashrc. Perhaps privoxy|tors left something in /etc? That's why it won't connect.[/QUOTE]

Yes, I saw that line just after I posted.

When/where might that env variable be set.  Where is the conf file stored.  I will go in and comment that line and try again.  See if it writes it again on reboot/login.

Thanks for your help an patience (even through some of my frustration).  Looks like you and ubuntu_demon almost hae this fixed.

---

### Post by llamakc on 2006-06-04
Well if there's not a setting in your .bashrc for a proxy, then its somewhere in /etc.  I'd look in ~/.bashrc first, and any files it sources (.bash_aliases for example). Next I'd look in /etc at /etc/privoxy/* or whatever is in /etc/ that privoxy may have owned.

You can do a `dpkg -L privoxy` to see all of the files that the package privoxy installed.

To test it, I'd log in as a 2nd user (after you create one) and see if that same line is in their `env` output. On the page: 

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=privoxy&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=privoxy&version=breezy&arch=i386)

There appears to be an /etc/privoxy/ directory. Did you do a `dpkg --purge privoxy` yet? I'd do that and logout/login again.

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]Well if there's not a setting in your .bashrc for a proxy, then its somewhere in /etc.  I'd look in ~/.bashrc first, and any files it sources (.bash_aliases for example). Next I'd look in /etc at /etc/privoxy/* or whatever is in /etc/ that privoxy may have owned.

You can do a `dpkg -L privoxy` to see all of the files that the package privoxy installed.

To test it, I'd log in as a 2nd user (after you create one) and see if that same line is in their `env` output. On the page: 

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=privoxy&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=privoxy&version=breezy&arch=i386)

There appears to be an /etc/privoxy/ directory. Did you do a `dpkg --purge privoxy` yet? I'd do that and logout/login again.[/QUOTE]


Ahh...not privoxy related, Gnome related.  New problem.  

It seems my system was set up to use a proxy.  Manual proxy configuration is checked. (I never set this up, somehow upgrade related).  I did not know the tool existed until I just started poking around in the system menu, saw proxy and decided to take a peek.  

But, new problem.

> 
sudo gnome-network-preferences

The application "gnome-network-preferences" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.

Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/proxy/mode' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/http_proxy/use_http_proxy' set in a read-only source at the front of your configuration path

---

### Post by llamakc on 2006-06-04
Some package owns those files. You can determine that with:'

sudo dpkg -S use_http_proxy

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]Some package owns those files. You can determine that with:'

sudo dpkg -S use_http_proxy[/QUOTE]

sudo dpkg -S use_http_proxy
dpkg: *use_http_proxy* not found.

And of course, my first thought was permissions.  There is no system in the root directory. /system

---

### Post by llamakc on 2006-06-04
This is a new install on machine that was not running Linux before? Or are there files around from old installations? I believe that /system/ stuff could be a gconf thing.

If you're okay with this, what about moving your .gconf and .gconfd to somewhere temporarily and relogging in to see if that variable is still in your `env`?

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]This is a new install on machine that was not running Linux before? Or are there files around from old installations? I believe that /system/ stuff could be a gconf thing.

If you're okay with this, what about moving your .gconf and .gconfd to somewhere temporarily and relogging in to see if that variable is still in your `env`?[/QUOTE]

It is an upgrade from a working Breezy to a working Dapper with a broken apt due to a weird http proxy setting, lol.

Moved gconf gconfd to gconf.old gconfd.old, logged out and in, htt proxy setting still in env.  Some of my Gnome settings are gone, so it worked.

It should be a simple thing though, right.  Deselect use http proxy in the gnome network proxy settings and select direct internet connection.  But somehow that setting is locked.

---

### Post by llamakc on 2006-06-04
If you do CTRL-ALT-F2 and go to an empty new terminal, login as your admin user, is it still there? If not, run apt-get from there.

What's weird is your problem is unique so far.

---

### Post by llamakc on 2006-06-04
You purged privoxy, right?

---

### Post by bmagill on 2006-06-04
[QUOTE=llamakc]You purged privoxy, right?[/QUOTE]

I did, but just to make certain...

```
sudo dpkg --purge privoxy
Password:
dpkg - warning: ignoring request to remove privoxy which isn't installed.
```

The proxy setting is not there when I login to a new TTY. CTRL-ALT-F2 a

and I was just able to update apt there.  I still cannot install via the GUI of course.

---

### Post by bmagill on 2006-06-04
Well, some progress.  I installed deboprphan via the TTY.

All of the r-carn stuff is related to statistical analysis software.  SHouldn;t play with server settings.  Thought I would say as it is likely unfamiliar.
```

xserver-common
r-cran-foreign
openoffice.org2
libdirac0
libnotify0
gstreamer0.8-wavpack
base-config
r-cran-cluster
libhk-kdeclasses7
hplip-base
nvidia-settings
r-cran-boot
r-cran-rpart
r-cran-design
screem
mozplugger
libgnomecupsui1.0-1
libgksu1.2-0
libnautilus-burn2
r-cran-rcmdr
gnomemeeting
xchat
libcamel1.2-6
r-cran-kernsmooth
libgksuui1.0-0
```

And here debfoster
```

 sudo debfoster -q
 cat /var/lib/debfoster/keepers
aalib1
autoconf
banshee
beep-media-player
build-essential
cupsys-driver-gimpprint
dash
db4.2-util
debfoster
ez-ipupdate
ffmpeg
firestarter
flashplayer-mozilla
foomatic-db-gimp-print
free-java-sdk
g77
gdk-imlib1
gij
gij-4.0
gnomebaker
gnucash
gphoto2
groff
gstreamer0.8-ffmpeg
gstreamer0.8-pitfdll
gstreamer0.8-plugins-multiverse
gtkam
gtkpod
gxine
ijsgimpprint
installation-report
irssi-text
java-gcj-compat
kaffeine
kamera
kcontrol
kile
kmymoney2
knoda
lame
language-pack-gnome-en
laptop-mode
latex-xft-fonts
linux-386
linux-image-2.6.12-10-k7
linux-restricted-modules-2.6.12-10-386
linux-restricted-modules-2.6.12-9-386
mjpegtools
mozilla-acroread
mozilla-mplayer
mplayer-586
mplayer-fonts
msttcorefonts
mysql-admin
mysql-navigator
numlockx
nvidia-glx
octave
odbcinst1debian1
ogle-gui
pan
planner
postgresql
postgresql-dev
preview-latex-style
procmail
python-gdchart
python-gst
python-musicbrainz
python-osd
python-pythoncard
python-wxglade
python2.4-pypoker-eval
qt3-apps-dev
r-base
r-cran-abind
r-cran-acepack
r-cran-car
r-cran-dbi
r-cran-gregmisc
r-cran-lmtest
r-cran-multcomp
r-cran-relimp
r-cran-rgl
r-cran-sm
r-cran-strucchange
r-omegahat-ggobi
rar
realplay
scigraphica
sox
subversion
sun-j2re1.5
sun-j2sdk1.5
timidity-interfaces-extra
tk8.4-dev
tora
ttf-arphic-bkai00mp
ttf-arphic-bsmi00lp
ttf-arphic-gbsn00lp
ttf-arphic-gkai00mp
tth
ubuntu-base
ubuntu-desktop
unace
unrar-nonfree
vlc-plugin-esd
vlc-plugin-glide
vlc-plugin-sdl
vlc-plugin-svgalib
vorbis-tools
w32codecs
webmin
wine
x11proto-gl-dev
xfonts-intl-european
xlibs-static-dev
xmms
xserver-xorg-driver-all
xserver-xorg-driver-glide
xserver-xorg-input-acecad
xserver-xorg-input-aiptek
xserver-xorg-input-all
xserver-xorg-input-calcomp
xserver-xorg-input-citron
xserver-xorg-input-digitaledge
xserver-xorg-input-dmc
xserver-xorg-input-dynapro
xserver-xorg-input-fpit
xserver-xorg-input-hyperpen
xserver-xorg-input-magellan
xserver-xorg-input-microtouch
xserver-xorg-input-mutouch
xserver-xorg-input-palmax
xserver-xorg-input-penmount
xserver-xorg-input-spaceorb
xserver-xorg-input-summa
xserver-xorg-input-tek4957
xserver-xorg-input-void
```

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=bmagill]I don't have either of these installed and in its current state, apt-get is uncooperative.  Can I download the .debs?[/QUOTE]
So that everybody who reads this knows : you can download packages also directly from from packages.ubuntu.com

Please post your "dpkg -l" too. You can do this in two ways ::
$ dpkg -l
$ dpkg -l > *filename*

install also gtkorphan from packages.ubuntu.com or :
$sudo apt-get install gtkorphan 
run gtkorphan,find all leftover configuration files with it,write them down and report than to and and purge them :
$sudo gtkorphan
click options -> show uninstalled packages with orphaned configuration files, mark them, write them down and report than to us and remove them

here something I found which might be related :
```

$dpkg -S  http_proxy
libgnomevfs2-common: /usr/share/gconf/schemas/system_http_proxy.schemas
$ apt-cache rdepends libgnomevfs2-common
Reverse Depends:
 |qalc
 |gnome-vfs-extfs
  libgnomevfs2-extra
  libgnomevfs2-extra
  libgnomevfs2-bin
  libgnomevfs2-0
  libgnomevfs2-0

```

Some of these packages may be installed. Let's try to purge them :
$sudo apt-get remove qalc gnome-vfs-extfs libgnomevfs2-common --purge

Also try booting into recovery mode and see if it works from there :
$sudo reboot
$sudo apt-get update

---

### Post by mybeat on 2006-06-05
i have the same problem
i did a clean install of dapper server
im behind linksys wrt54gl router 
my env doesnt have a proxy nor there are any proxy running
i have tried clean sources.list from url in this thread
i can ping and wget from those urls that apt says connection to failed

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=mybeat]i have the same problem
i did a clean install of dapper server
im behind linksys wrt54gl router 
my env doesnt have a proxy nor there are any proxy running
i have tried clean sources.list from url in this thread
i can ping and wget from those urls that apt says connection to failed[/QUOTE]
Please try all suggestions and report them back. We want to see everything configurationfiles , log files and errors :).

---

### Post by ubuntu_demon on 2006-06-05
add a new user :system->adminstration->users and groups

give this user all the permissions, logout from your current user, log in to the new user and try if the problem remains.

---

### Post by mybeat on 2006-06-05
here's my sources.list
```


# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

```
i have these error's 
```

zion@jungle:/etc/apt$ sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Ign http://archive.ubuntu.com dapper-updates/main Packages
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
env
```
zion@jungle:~$ env
TERM=xterm
SHELL=/bin/bash
SSH_CLIENT=192.168.1.100 4876 22
SSH_TTY=/dev/pts/0
USER=zion
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
MAIL=/var/mail/zion
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
PWD=/home/zion
LANG=en_US.UTF-8
HISTCONTROL=ignoredups
SHLVL=1
HOME=/home/zion
LANGUAGE=en
LOGNAME=zion
SSH_CONNECTION=192.168.1.100 4876 192.168.1.111 22
LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

```
my resolv.conf
```

nameserver 192.168.1.1
nameserver 4.2.2.2
nameserver 192.168.1.123

```
route
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         zion            0.0.0.0         UG    0      0        0 eth0

```
```

eth0      Link encap:Ethernet  HWaddr 00:07:E9:9B:60:D2
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe9b:60d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:392580 (383.3 KiB)  TX bytes:297206 (290.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
i dont have /etc/interfaces..
heres hosts and hostname 
```

zion@jungle:/etc$ cat hosts
127.0.0.1       localhost
192.168.1.111   jungle

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
zion@jungle:/etc$ cat hostname
jungle

```
apt-get remove -f 
```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
doing apt-get update..
same errors

uname -a
Linux jungle 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux
after etc/init.d/networking restart
```

zion@jungle:/etc/init.d$ sudo ./networking restart
 * Reconfiguring network interfaces...                                                               [ ok ]
zion@jungle:/etc/init.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:9B:60:D2
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe9b:60d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:455283 (444.6 KiB)  TX bytes:378533 (369.6 KiB)


```
rebooted
apt-get still same errors
i can ping n wget
i only have console

---

### Post by llamakc on 2006-06-05
I dunno where your at but I have us.archive in my sources.list. Maybe adding a country code would help?

---

### Post by llamakc on 2006-06-05
ken@vulva:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#deb [http://ato.netsons.org/ubuntu/](http://ato.netsons.org/ubuntu/) binary/


deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./


Ignore the unofficial lines added by EasyUbuntu

---

### Post by mybeat on 2006-06-05
tried llamakc's sources.list
same errors :/
country code doesnt work either

---

### Post by llamakc on 2006-06-05
Safe to say you've powercycled your router?

---

### Post by mybeat on 2006-06-05
powercycled?

---

### Post by llamakc on 2006-06-05
Turned it off and then back on. Then renew your dhcp lease with another /etc/init.d/networking restart

Can you get to websites by name with w3m? like w3m [http://ubuntuforums.org?](http://ubuntuforums.org?)

---

### Post by mybeat on 2006-06-05
havent turned it of and on
yes i can w3m to ubuntuforums.org
and i have a static ip i dont use dhcp atm
but tried with dhcp also had same problem

---

### Post by mybeat on 2006-06-05
found out a solution from this thread
[http://ubuntuforums.org/showthread.php?t=189383](http://ubuntuforums.org/showthread.php?t=189383)

---

### Post by smoothdave on 2006-06-05
I've been beating my head against this one myself all weekend.  Here's what I've got. I had a Breezy Ubuntu machine working fine in VMWare.  I did a dist-upgrade.  That virtual machine uses apt-get perfectly.  I then attempted to install kubuntu and xubuntu onto VMWare virtual machines from both the Desktop and Alternate iso images.  On install, the installer complained about being unable to connect for security updates.

Once the machines were up and running, I attempted virtually everything offered above, plus a few other things.  I got all of the issues described above on absolutely clean installs of kubuntu and xubuntu.  Finally, I found this thread and the advice to edit my sources.list changing all references from http to ftp.  After doing that, I was finally able to run apt-get to install needed software.

I'm working nicely now with the changes, but something is not quite right.

Thank you.

Smooth Dave

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=mybeat]
i have these error's 
```

zion@jungle:/etc/apt$ sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Ign http://archive.ubuntu.com dapper-updates/main Packages
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
[/QUOTE]

It's not trying to connect to localhost and there's nothing about a proxy in your env. Your problem might be related to bmagill's problem but it's different.

[QUOTE=mybeat]
i dont have /etc/interfaces..
[/QUOTE]

You've discovered a typo by me :). I meant : 
/etc/network/interfaces

[QUOTE=mybeat]
uname -a
Linux jungle 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux
[/QUOTE]

Why are you running a server kernel ? Are you running this on purpose ?

Or maybe you upgraded a normal Ubuntu installation with a Dapper server cd by accident ?

[QUOTE=mybeat]
rebooted
apt-get still same errors
i can ping n wget
i only have console[/QUOTE]

If you install from a server cd you won't get a graphical environment. It's possible though to install it (for example xubuntu-desktop).

---

### Post by ubuntu_demon on 2006-06-06
Please try this :
[http://www.ubuntuforums.org/showpost.php?p=1101134&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1101134&postcount=9)
from this thread :
[http://www.ubuntuforums.org/showthread.php?t=189383](http://www.ubuntuforums.org/showthread.php?t=189383)

And post the errors.

---

### Post by smoothdave on 2006-06-06
Per the instructions, I tried to comment out the line:

Acquire::http::Proxy "false";

from the file apt.conf.  I then edited the sources.list file returning all of the ftp's to http.

Using the usual # sign caused an error when I tried apt-get update, so I removed that line from apt.conf and tried again.  At that point, apt-get update worked normally.

So, we now have two solutions.  One is to replace all occurances of http with ftp in the sources.list file.  Two is to remove the above line from apt.conf.

Something is awry.

Thank you for your help.

Smooth Dave

---

### Post by smoothdave on 2006-06-06
One more thing.  I had a Breezy Ubuntu install that I updated by switching sources.list from breezy to dapper and then running apt-get dist-upgrade.  That machine never had a problem running apt-get even after being updated to dapper.  That machine doesn't have an apt.conf file in /etc/apt.

Smooth Dave

---

### Post by ubuntu_demon on 2006-06-07
Okay now we know how to solve it. But we don't know the cause of the problem. I have the same line in my /etc/apt/apt.conf without having any problems :
```

Acquire::::Proxy "false";

```

---

