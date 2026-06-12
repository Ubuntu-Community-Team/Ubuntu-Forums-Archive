---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by manukeerampanal on 2015-03-15
[COLOR=#444444][FONT=proxima-nova]Hi, 
When I tried to update my vps loaded with Ubuntu 14.04 LTS  using the commands '**apt-get update**' and '**apt-get upgrade**', **I got following error. **
--------------------------------------------START--------------------------------------------------------- 
Errors were encountered while processing: 
/var/cache/apt/archives/libc-bin_2.19-0ubuntu6.6_amd64.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
----------------------------------------------END-----------------------------------------------------------

[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]**The file source.list conatins the following content : **
--------------------------------------------START--------------------------------------------------------- 
root@manu:/etc/apt# vim sources.list 
deb-src [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty universe 
deb [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-updates universe 
deb-src [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-updates universe[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty multiverse 
deb-src [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty multiverse 
deb [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-updates multiverse 
deb-src [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-updates multiverse[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-backports main restricted universe multiverse 
deb-src [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-backports main restricted universe multiverse[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]## Uncomment the following two lines to add software from Ubuntu's 
## 'extras' repository. 
## This software is not part of Ubuntu, but is offered by third-party 
## developers who want to ship their latest software. 
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main 
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main 
#deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) jessie main contrib non-free 
----------------------------------------------END-----------------------------------------------------------

[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]**The entire response for the above commands are as follows :**[/FONT][/COLOR]
[COLOR=#444444][FONT=proxima-nova]--------------------------------------------START--------------------------------------------------------- 
root@manu:~# apt-get update 
Ign [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty InRelease 
Ign [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates InRelease 
Ign [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports InRelease 
Get:1 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty Release.gpg [933 B] 
Get:2 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates Release.gpg [933 B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease 
Get:3 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports Release.gpg [933 B] 
Get:4 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty Release [58.5 kB] 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B] 
Get:6 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates Release [62.0 kB] 
Get:7 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports Release [62.0 kB] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB] 
Get:9 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/main Sources [1064 kB] 
Get:10 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/restricted Sources [5433 B] 
Get:11 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/universe Sources [6399 kB] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [72.1 kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2061 B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [17.9 kB] 
Get:15 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/multiverse Sources [174 kB] 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1905 B] 
Get:17 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/main amd64 Packages [1350 kB] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [222 kB] 
Get:19 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/restricted amd64 Packages [13.0 kB] 
Get:20 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/universe amd64 Packages [5859 kB] 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8875 B] 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [88.0 kB] 
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3459 B] 
Get:24 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/multiverse amd64 Packages [132 kB] 
Get:25 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/main i386 Packages [1348 kB] 
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [212 kB] 
Get:27 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/restricted i386 Packages [13.4 kB] 
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8846 B] 
Get:29 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/universe i386 Packages [5866 kB] 
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [87.9 kB] 
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3628 B] 
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [113 kB] 
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [1580 B] 
Get:34 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/multiverse i386 Packages [134 kB] 
Get:35 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/main Translation-en [762 kB] 
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [2266 B] 
Get:37 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/multiverse Translation-en [102 kB] 
Get:38 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/restricted Translation-en [3457 B] 
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [48.8 kB] 
Get:40 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty/universe Translation-en [4089 kB] 
Get:41 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/main Sources [183 kB] 
Get:42 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/restricted Sources [2564 B] 
Get:43 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/universe Sources [107 kB] 
Get:44 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/multiverse Sources [4484 B] 
Get:45 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/main amd64 Packages [449 kB] 
Get:46 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/restricted amd64 Packages [9238 B] 
Get:47 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/universe amd64 Packages [258 kB] 
Get:48 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/multiverse amd64 Packages [11.2 kB] 
Get:49 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/main i386 Packages [439 kB] 
Get:50 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/restricted i386 Packages [9256 B] 
Get:51 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/universe i386 Packages [259 kB] 
Get:52 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/multiverse i386 Packages [11.3 kB] 
Get:53 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/main Translation-en [214 kB] 
Get:54 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/multiverse Translation-en [5508 B] 
Get:55 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/restricted Translation-en [2433 B] 
Get:56 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-updates/universe Translation-en [132 kB] 
Get:57 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/main Sources [5298 B] 
Get:58 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/restricted Sources [28 B] 
Get:59 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/universe Sources [22.1 kB] 
Get:60 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/multiverse Sources [1898 B] 
Get:61 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/main amd64 Packages [5536 B] 
Get:62 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/restricted amd64 Packages [28 B] 
Get:63 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/universe amd64 Packages [25.8 kB] 
Get:64 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/multiverse amd64 Packages [1245 B] 
Get:65 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/main i386 Packages [5550 B] 
Get:66 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/restricted i386 Packages [28 B] 
Get:67 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/universe i386 Packages [25.8 kB] 
Get:68 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/multiverse i386 Packages [1249 B] 
Get:69 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/main Translation-en [3233 B] 
Get:70 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/multiverse Translation-en [776 B] 
Get:71 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/restricted Translation-en [14 B] 
Get:72 [http://mirrors.digitalocean.com](http://mirrors.digitalocean.com) trusty-backports/universe Translation-en [23.9 kB] 
Fetched 30.7 MB in 17s (1736 kB/s) 
Reading package lists... Done 
root@manu:~# apt-get upgrade 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
Calculating upgrade... Done 
The following packages have been kept back: 
linux-generic linux-headers-generic linux-image-generic 
The following packages will be upgraded: 
apache2 apache2-bin apache2-data apparmor apport apt-transport-https 
apt-utils bind9-host ca-certificates cloud-guest-utils cloud-init cpio curl 
dbus dnsutils file krb5-locales landscape-common language-pack-en 
language-pack-en-base libapache2-mod-php5 libapparmor1 libapt-inst1.5 
libbind9-90 libblkid1 libc-bin libcgmanager0 libcomerr2 libcurl3 
libcurl3-gnutls libdbus-1-3 libdns100 libdrm2 libelf1 libevent-2.0-5 
libfreetype6 libglib2.0-0 libglib2.0-data libgssapi-krb5-2 libicu52 libisc95 
libisccc90 libisccfg90 libk5crypto3 libkrb5-3 libkrb5support0 liblwres90 
libmagic1 libmount1 libmysqlclient18 libnuma1 libpam-systemd libplymouth2 
libprocps3 libsepol1 libss2 libssl1.0.0 libsystemd-daemon0 libsystemd-login0 
libudev1 libuuid1 libxml2 libyaml-0-2 linux-firmware lshw mime-support 
multiarch-support mysql-client-5.5 mysql-client-core-5.5 mysql-common 
mysql-server mysql-server-5.5 mysql-server-core-5.5 ntpdate openssl php5 
php5-cli php5-common php5-gd php5-mysql php5-readline plymouth 
plymouth-theme-ubuntu-text ppp procps python-apt python-apt-common 
python-requests python-urllib3 python-yaml python3-apport python3-apt 
python3-distupgrade python3-problem-report python3-software-properties 
rsyslog software-properties-common systemd-services tcpdump 
ubuntu-release-upgrader-core udev unattended-upgrades update-notifier-common 
uuid-runtime wget wpasupplicant 
106 upgraded, 0 newly installed, 0 to remove and 3 not upgraded. 
Need to get 0 B/54.9 MB of archives. 
After this operation, 293 kB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
Extracting templates from packages: 100% 
Preconfiguring packages ... 
(Reading database ... 95095 files and directories currently installed.) 
Preparing to unpack .../libc-bin_2.19-0ubuntu6.6_amd64.deb ... 
Unpacking libc-bin (2.19-0ubuntu6.6) over (2.19-0ubuntu6.3) ... 
dpkg: error processing archive /var/cache/apt/archives/libc-bin_2.19-0ubuntu6.6_amd64.deb (--unpack): 
trying to overwrite '/usr/sbin/update-locale', which is also in package locales 2.19-13 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
Errors were encountered while processing: 
/var/cache/apt/archives/libc-bin_2.19-0ubuntu6.6_amd64.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
----------------------------------------------END-----------------------------------------------------------[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-03-15
> **manukeerampanal said:**
> 
Unpacking libc-bin (2.19-0ubuntu6.6) over (2.19-0ubuntu6.3) ... 
dpkg: error processing archive /var/cache/apt/archives/libc-bin_2.19-0ubuntu6.6_amd64.deb (--unpack): 
trying to overwrite '/usr/sbin/update-locale', which is also in package locales 2.19-13 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 

You have two packages that *conflict*. They cannot both be installed. One must be uninstalled.
locales 2.19-13
libc-bin 2.19-0ubuntu6.6

The system cannot decide which of those two must be removed. You, the human, must make the choice.
This kind of problem sometimes happens with PPA or other non-Ubuntu package sources. Packages in the official Ubuntu repositories don't have this problem; testing weeds it out. 

Let's see if your problem is due to non-Ubuntu packages:

```
$ rmadison libc-bin | grep trusty-updates
 libc-bin | **2.19-0ubuntu6.6**    | trusty-updates           | amd64, arm64, armhf, i386, powerpc, ppc64el
$ rmadison locales | grep trusty-updates
 locales | **2.13+git20120306-12.1** | trusty-updates           | all
```

Ah, there's the problem - your 'locales' package is from a non-Ubuntu source. 2.19.13 instead of 2.13+git20120306-12.1
Wherever you got it from built it in a way that caused the conflict.

There are three ways to fix the problem:

1) Contact the maintainer of wherever you got that lousy 'locales' package from and get them to fix the package. The next update will fix your system. This is the easiest and safest way.

2) Uninstall locales, disable the source you got it from, rebuild your package database, and install the older version of locales from the Ubuntu repositories. This is the fastest way to fix the problem, but not the easiest.

3) Reinstall. This is an option of last resort. It should not be necessary.

If you need further help with any of these options, let us know which option you want to do.

---

### Post by manukeerampanal on 2015-03-16
It will be great if you could help me to go through the 2nd option.
[B]
"[/B]*Uninstall locales, disable the source you got it from, rebuild your  package database, and install the older version of locales from the  Ubuntu repositories.***"**

---

### Post by ian-weisser on 2015-03-16
First, use 'apt-cache policy' to discover which source needs to be removed.
Example - yours will look a bit different :
```
$ **apt-cache policy locales**
locales:
  Installed: 2.13+git20120306-17
  Candidate: 2.13+git20120306-17
  Version table:
 *** 2.13+git20120306-17 0
        500** http://us.archive.ubuntu.com/ubuntu/ utopic/main** amd64 Packages
        100 /var/lib/dpkg/status
```

Second, disable (comment out) that source in /etc/apt/sources.list.d/

Third, 
```
sudo apt-get clean locales      ## Delete the package from your system's cache, so the system doesn't promptly reinstall it.
sudo apt-get update             ## Rebuild your system's package database without the removed source.
sudo apt-get remove locales     ## Uninstall the old 'locales' package
sudo apt-get install locales    ## Download and install a new (Ubuntu) version of the 'locales' package
```

If you have any questions, encounter any problems, or run into error messages, then STOP. Post here.

---

### Post by manukeerampanal on 2015-03-19
The last command is giving me some error... It looks like as follows :

*root@manu:~# sudo apt-get install locales*
*Reading package lists... Done*
*Building dependency tree*
*Reading state information... Done*
*Some packages could not be installed. This may mean that you have*
*requested an impossible situation or if you are using the unstable*
*distribution that some required packages have not yet been created*
*or been moved out of Incoming.*
*The following information may help to resolve the situation:*

*The following packages have unmet dependencies:*
* locales : Depends: libc6 (>= 2.9-0ubuntu10) but it is not going to be installed or*
*                    libc6.1 (>= 2.9-0ubuntu10) but it is not installable*
[I]E: Unable to correct problems, you have held broken packages.


[/I]
The following is what happens when I execute the command ***apt-cache policy locales ***&#8203;:

*root@manu:~# apt-cache policy locales*
*locales:*
*  Installed: (none)*
*  Candidate: 2.13+git20120306-12.1*
*  Version table:*
*     2.19-13 0*
*        100 /var/lib/dpkg/status*
*     2.13+git20120306-12.1 0*
*        500 [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty-updates/main amd64 Packages*
*     2.13+git20120306-12 0*
*        500 [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/) trusty/main amd64 Packages*

---

### Post by ian-weisser on 2015-03-19
Take a look at apt-cache policy for libc6 and libc6.1
The error message indicates that neither of those packages can be installed, which is in turn blocking locales.

---

### Post by asaadirfans on 2015-10-12
[COLOR=#DD1144][FONT=Menlo]I;m facing a similar problem with ubuntu 12.04.5  when i try to do this:

sudo apt-get -f install


I get the following error:

[/FONT][/COLOR][COLOR=#000000][COLOR=#000000]asaad@VAIO:~$ sudo apt-get -f install[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Reading package lists... Done[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Building dependency tree [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Reading state information... Done[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Correcting dependencies... Done[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]The following packages will be REMOVED:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]libopenni-nite-dev[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]After this operation, 0 B of additional disk space will be used.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Do you want to continue [Y/n]? y[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000](Reading database ... 579300 files and directories currently installed.)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Removing libopenni-nite-dev ...[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Failed: Error![/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]dpkg: error processing libopenni-nite-dev (--remove):[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]subprocess installed pre-removal script returned error exit status 255[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]No apport report written because MaxReports is reached already[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Errors were encountered while processing:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]libopenni-nite-dev[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/COLOR]

---

### Post by ian-weisser on 2015-10-12
> **asaadirfans said:**
> 
[COLOR=#000000][COLOR=#000000]Removing libopenni-nite-dev ...[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Failed: Error![/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]dpkg: error processing libopenni-nite-dev (--remove):[/COLOR][/COLOR]
[B][COLOR=#000000][COLOR=#000000]subprocess installed pre-removal script returned error exit status 255[/COLOR][/COLOR]
[/B][COLOR=#000000][COLOR=#000000]No apport report written because MaxReports is reached already[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Errors were encountered while processing:[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]libopenni-nite-dev[/COLOR][/COLOR]


They may (understandably) seem similar you you, but they are not.
Your issue is different, and unrelated to the original poster in this thread.
Please open a separate thread for your issue.

---

