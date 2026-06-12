---
title: "Installing GCC"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by darkbluesea on 2006-10-21
've just installed a brand new ubuntu, and sucessfuly upgraded from 5'10 to 6'10, but when I:

dark@onix:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
gcc: Depends: gcc-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages
dark@onix:~$

also:
sudo apt-get update
sudo apt-get -f update

They work fine but simply dont install gcc, and 

sudo apt-get install build-essential
---
dark@onix:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
---
Doesn work,  How to overcome this? I've tried finding severeal solutions on the forum's, but none that actualy worked.

---

### Post by lloyd_b on 2006-10-21
I ran into that one the first time I tried to compile something.  In my case, gcc was there, but libc6-dev wasn't, so no headers in "/usr/include".

Try "apt-get install libc6-dev", then try the "apt-get install build-essential" again.

Lloyd B.

---

### Post by lord_Kalaeth on 2006-11-04
Hey! 
I'm not really new to ubuntu ('ve been using it for a coulpe of years in college), but just recentely I installed 6.10 here at home. I've been trying to get gcc to work, for a couple of days now.. but I cant -_- Whenever I do "sudo aptitude update" I get this :

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://pt.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://pt.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://pt.archive.ubuntu.com dapper Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://pt.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security Release
Ign http://pt.archive.ubuntu.com dapper/main Packages
Hit http://pt.archive.ubuntu.com dapper/restricted Packages
Hit http://pt.archive.ubuntu.com dapper/main Sources
Hit http://pt.archive.ubuntu.com dapper/restricted Sources
Hit http://pt.archive.ubuntu.com dapper-updates/main Packages
Hit http://pt.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://pt.archive.ubuntu.com dapper-updates/main Sources
Hit http://pt.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://security.ubuntu.com dapper-security/main Packages
Get:4 http://pt.archive.ubuntu.com dapper/main Packages [821kB]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
99% [4 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://pt.archive.ubuntu.com dapper/main Packages
  Sub-process gzip returned an error code (1)
Get:5 http://security.ubuntu.com dapper-security/main Packages [98.4kB]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://security.ubuntu.com dapper-security/main Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 1s (4B/s)
Reading package lists... Done

```

and after that when I try : "sudo aptitude install build-essential" I get this :

```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "build-essential"
The following packages have been kept back:
  cpio language-pack-en language-pack-gnome-en linux-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-386
  linux-restricted-modules-common xserver-xorg-core
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by lloyd_b on 2006-11-04
I can't really tell, but at first glance it looks like a problem with Aptitude.

Try this instead:

```
[B]sudo apt-get install build-essential
[/B]
```
Post any errors/warnings you get from that.

Lloyd B.

---

### Post by lord_Kalaeth on 2006-11-05
I had tried before with "sudo apt-get update" :

```
Get:1 http://pt.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://pt.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://pt.archive.ubuntu.com dapper Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://pt.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security Release
Ign http://pt.archive.ubuntu.com dapper/main Packages
Hit http://pt.archive.ubuntu.com dapper/restricted Packages
Hit http://pt.archive.ubuntu.com dapper/main Sources
Hit http://pt.archive.ubuntu.com dapper/restricted Sources
Hit http://pt.archive.ubuntu.com dapper-updates/main Packages
Hit http://pt.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://pt.archive.ubuntu.com dapper-updates/main Sources
Hit http://pt.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://security.ubuntu.com dapper-security/main Packages
Get:4 http://pt.archive.ubuntu.com dapper/main Packages [821kB]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:5 http://security.ubuntu.com dapper-security/main Packages [98.4kB]
99% [4 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://pt.archive.ubuntu.com dapper/main Packages
  Sub-process gzip returned an error code (1)
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://security.ubuntu.com dapper-security/main Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 1s (3B/s)
Failed to fetch http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
and then :  sudo apt-get install build-essential
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential

```

thnks anyway o/

---

### Post by studiesrule on 2006-11-05
Are you running a x86_64 system? I used to get the :  
Sub-process gzip returned an error code (1)
when I installed the x86_64 version. I didn't have the problem with the i386 package.

---

### Post by lord_Kalaeth on 2006-11-05
'm runing the i386...
now I tryed the Synaptic Package Manager, and got the same :
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

---

### Post by studiesrule on 2006-11-05
This doesn't really help, but that linke (minus the ':') can be viewed in my browser (I don't get it). But i downloaded it anyway, and i can unzip it. Perhaps it hasn't been compressed at all?

---

### Post by lord_Kalaeth on 2006-11-05
don't know what the real problem was, but I updated the source list to the one in [this link]("http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2"), and now it works.. Guess the pt source list was now well.. 

Thanks ppl ;) o/

---

### Post by marmiteOlz on 2006-11-06
k my prob.. if its related at all...
while trying to install my nvidia g card drivers i typed in sudo apt-get install linux-kernel-headers build-essential
to which i was at some point told my cc wasnt in the path,, im sure  and pointed me to gcc package
i am 2 days old at ubuntu,, 1st day i managed to remove any video drivers unsure how but boot said need gdm reinstall..
anyway 
this is the reply i get when i type sudp apt-get build-essential and teh following codes...
i did install the gcc package with libc6-dev  files, as it recommended to me
should it return a unable to lock value??


marmite@marmite-desktop:~$ sudo apt-get install libc6-dev
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
marmite@marmite-desktop:~$


update...

marmite@marmite-desktop:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 0s (9B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
marmite@marmite-desktop:~$


btw  even just the brown ubuntu theme has me won over

---

### Post by marmiteOlz on 2006-11-06
k  told u i was new](*,) 

a quick reboot   fixed the unable to lock  problem
sorry guys

---

