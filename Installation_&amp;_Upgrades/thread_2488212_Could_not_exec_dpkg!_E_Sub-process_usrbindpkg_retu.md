---
title: "Could not exec dpkg! E: Sub-process /usr/bin/dpkg returned an error code (100)"
date: 2023-06-27
forum: Installation &amp; Upgrades
---

### Post by jiansoco27 on 2023-06-27
Hi,

I'm new to linux.

When I am installing this "sudo apt-get install wget libnss3-tools -y"

I am getting this error at the end:
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

Please see below the whole installation message
```
root@LAPTOP-VPV77LD5:/usr/bin# sudo apt-get install wget libnss3-tools -yReading package lists... DoneBuilding dependency tree... DoneReading state information... Donewget is already the newest version (1.21.2-2ubuntu1).The following additional packages will be installed:  libnspr4 libnss3The following NEW packages will be installed:  libnspr4 libnss3 libnss3-tools0 upgraded, 3 newly installed, 0 to remove and 57 not upgraded.Need to get 1963 kB of archives.After this operation, 6412 kB of additional disk space will be used.Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 libnspr4 amd64 2:4.32-3build1 [119 kB]Get:2 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnss3 amd64 2:3.68.2-0ubuntu1.2 [1280 kB]Get:3 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 libnss3-tools amd64 2:3.68.2-0ubuntu1.2 [565 kB]Fetched 1963 kB in 3s (776 kB/s)Could not exec dpkg!E: Sub-process /usr/bin/dpkg returned an error code (100)
```


ls -l dpkg
```
-rwxr-xr-x 1 root root 260328 Jun 27 19:41 dpkg
```

---

### Post by Bashing-om on 2023-06-27
jiansoco27 - Hello

Not much info to work with - let's do a bit of poking see what we can learn.

Please post back the outputs of terminal commands:
```

lsb_release -a
sudo apt update
sudo apt upgrade
dpkg -l wget

```

*wget* I expect to be a default install.
 libnss3-tools is in the universe repo - is that repo enabled in your sources list ?
```

cat -n /etc/apt/sources.list

```

[INDENT]and a hunt'n we shall go
[/INDENT]

---

### Post by jiansoco27 on 2023-06-28
Hi Bashing-om

lsb_release -a
```
No LSB modules are available.Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:        22.04
Codename:       jammy
```


sudo apt update
```
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Hit:4 https://ppa.launchpadcontent.net/wslutilities/wslu/ubuntu jammy InRelease
Get:5 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [730 kB]
Get:7 http://archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [191 kB]
Get:8 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [15.3 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [459 kB]
Get:10 http://archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [71.0 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [932 kB]
Get:12 http://archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [199 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [40.9 kB]
Get:14 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse Translation-en [9684 B]
Fetched 2984 kB in 5s (607 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
57 packages can be upgraded. Run 'apt list --upgradable' to see them.
```


sudo apt upgrade
```
Reading package lists... DoneBuilding dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport bind9-dnsutils bind9-host bind9-libs binutils binutils-common binutils-x86-64-linux-gnu ca-certificates
  distro-info-data dpkg iptables libbinutils libcap2 libcap2-bin libctf-nobfd0 libctf0 libglib2.0-0 libglib2.0-bin
  libglib2.0-data libgssapi-krb5-2 libip4tc2 libip6tc2 libk5crypto3 libkrb5-3 libkrb5support0 libncurses6 libncursesw6
  libpam-cap libperl5.34 libpython3.10 libpython3.10-minimal libpython3.10-stdlib libssh-4 libssl3 libtinfo6
  libx11-data libxtables12 ncurses-base ncurses-bin openssl perl perl-base perl-modules-5.34 python3-apport
  python3-problem-report python3-software-properties python3.10 python3.10-minimal snapd software-properties-common
  tzdata vim vim-common vim-runtime vim-tiny wslu xxd
57 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
40 standard LTS security updates
Need to get 0 B/64.1 MB of archives.
After this operation, 78.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
```


dpkg -l wget
```
-bash: /usr/bin/dpkg: No such file or directory
```


cat -n /etc/apt/sources.list
```
     1  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to     2  # newer versions of the distribution.
     3  deb http://archive.ubuntu.com/ubuntu/ jammy main restricted
     4  # deb-src http://archive.ubuntu.com/ubuntu/ jammy main restricted
     5
     6  ## Major bug fix updates produced after the final release of the
     7  ## distribution.
     8  deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted
     9  # deb-src http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    10
    11  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12  ## team. Also, please note that software in universe WILL NOT receive any
    13  ## review or updates from the Ubuntu security team.
    14  deb http://archive.ubuntu.com/ubuntu/ jammy universe
    15  # deb-src http://archive.ubuntu.com/ubuntu/ jammy universe
    16  deb http://archive.ubuntu.com/ubuntu/ jammy-updates universe
    17  # deb-src http://archive.ubuntu.com/ubuntu/ jammy-updates universe
    18
    19  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    20  ## team, and may not be under a free licence. Please satisfy yourself as to
    21  ## your rights to use the software. Also, please note that software in
    22  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23  ## security team.
    24  deb http://archive.ubuntu.com/ubuntu/ jammy multiverse
    25  # deb-src http://archive.ubuntu.com/ubuntu/ jammy multiverse
    26  deb http://archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    27  # deb-src http://archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    28
    29  ## N.B. software from this repository may not have been tested as
    30  ## extensively as that contained in the main release, although it includes
    31  ## newer versions of some applications which may provide useful features.
    32  ## Also, please note that software in backports WILL NOT receive any review
    33  ## or updates from the Ubuntu security team.
    34  deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    35  # deb-src http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    36
    37  deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted
    38  # deb-src http://security.ubuntu.com/ubuntu/ jammy-security main restricted
    39  deb http://security.ubuntu.com/ubuntu/ jammy-security universe
    40  # deb-src http://security.ubuntu.com/ubuntu/ jammy-security universe
    41  deb http://security.ubuntu.com/ubuntu/ jammy-security multiverse
    42  # deb-src http://security.ubuntu.com/ubuntu/ jammy-security multiverse
```

---

### Post by Bashing-om on 2023-06-28
jiansoco27; Ouch -

does not look good for the home team:
> 
-bash: /usr/bin/dpkg: No such file or directory


Let's poke a bit deeper and confirm !
what returns:
```

ls -l /usr/bin/dpkg
which wget
which curl

```

-this might get real deep - quick-

---

### Post by MAFoElffen on 2023-06-28
Please do
```

file /usr/bin/dpkg  

```
The output should look like this for current 22.04.2
```

/usr/bin/dpkg: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=01c5c3579d7ff92ba50a59282257b14899515c82, for GNU/Linux 3.2.0, stripped

```
If you look at the size of /usr/bin/dpkg, this is what is current (which doesn't match with his, which shows as 260328) .
```

$ ls -l /usr/bin/dpkg
-rwxr-xr-x 1 root root 318144 Apr  1 06:43 /usr/bin/dpkg

```
Unfortunately, the other times I have seen this same error, it was a corrupted dpkg/apt system was fatal. The OS had to be reinstalled. You can't install, remove, reinstall without apt. You can NOT do apt, nor configure, nor reconfigure without dpkg. I do not know of a way to reinstall dpkg, if dpkg is not working... I have even tried to do that in a chroot, and it wouldn't work. It is at a certain level, were that doesn't work.

I am sorry to be the bearer of bad news. My condolences. Backup. Migrate to a new install.

---

### Post by MAFoElffen on 2023-06-28
It wouldn't let me edit the last post... Instead of migrating to fresh install, when you get to the panel in the attachment, do that. Backup everything first... Run the Ubuntu 'system-info' script in my signature line, and at the end of the report, there will be a list a User manually install packages, that you can use to reinstall any applications you installed beyond what was from the default install.

---

### Post by Bashing-om on 2023-06-28
double Ouchies !

Was afraid of that - MAFoElffen -
Racking my brains as to how one maybe *could* re-install dpkg. The master has spoken. No point on racking the brain any further.

Again:
Thanks MAFoElffen :D

---

### Post by jiansoco27 on 2023-06-28
Hi Bashing-om

ls -l /usr/bin/dpkg
```
-rwxr-xr-x 1 root root 260328 Jun 27 19:41 /usr/bin/dpkg
```

which wget
```
/usr/bin/wget
```

which curl
```
/usr/bin/curl
```

---

### Post by jiansoco27 on 2023-06-28
Hi MAFoElffen,

file /usr/bin/dpkg 

```
/usr/bin/dpkg: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.24, BuildID[sha1]=dcdf5422e53ea9394a067db13f46cc6d5bf1aab7, stripped
```


I am actually using Ubuntu WSL. Do I need to reinstall it?

Thank you

---

### Post by MAFoElffen on 2023-06-28
Using "Windows System for Linux" (WSL)  explains a whole lot in the output and differences. LOL.  You probably should have mentioned that in the first post. I know when I tested the UbuntuForums 'system-info' script against it... In the first section of the script, there is a check of require "basic Linux utilities" that are used in the script, that are mostly installed by default in Ubuntu, but that other distributions don't always have as a default... With WSL, a lot portion of those default utilities are gone. Or they use symlinks to Windows apps to try to make them 'compatible', so some of the utility options do not work. 

'dpkg' is a low level Linux utility in Ubuntu Base. If broken it cannot be reinstalled, because it would require using 'itself' to do it.

WSL is not installed via the Live Image Environment (L.I.E.) of the Installation ISO. It is installed through the Windows Store process. There is an install / uninstall process... But in your case, there is also are hidden repair and reset features, that are not really well documented anywhere...

Backup your data and figure out which applications you installed after the original install. This is going to be by looking at what is there, The APT system is a Debian branch wrapper for the 'dpkg' utility... So you are not going to be able to use either to help you with that. When you do migrations, the process is to backup your data, list your user installed applications, backup any configuration files you made changes to change settings for, and your User Home directories. Then you reinstall. Then you restores your data, install the User applications and configurations. Restore the home directories.

Search on this forum for "Backup" under Username "TheFu"... He has many great threads and posts on how to do backups of Ubuntu, and be able to migrate a system.

When you are ready, In Windows, Press the Win key > Open Settings >Open Apps Category > In the Apps and features section, use the Search Dialog box to search for "Ubuntu" > When it comes up, click on it with your mouse... A dialog box will pop up  with two Buttons: Move & Uninstall... Under the Application Description, there will be a link that says "Advanced Settings". Select that link. That will bring up another dialog Window. There will be two sections they we are interested in in that Window. One is for "Repair" and the other is "Reset".

First select "Repair". That will try to repair the installation, trying not to affect installed user applications and user data. Hopefully that works.

If it doesn't, then use the "Reset" button. Which will reinstall Ubuntu to a fresh newly installed state... In that state everything you did after the initial new state will be gone. Your User applications and Data will have to be reinstalled, reconfigured, and restored.

If that doesn't correct it, then use the same procedure above, but use the application Uninstall button. Then reinstall from the Windows Store.

Any questions?

EDIT: Just curious... Which Windows Edition? Pro? If Pro or above, have your though about turning on Hyper-V as a feature and installing a full blown Ubuntu VM Guest? I think you would get a lot better experience of what Ubuntu can be and is... Instead of the terminal environment of WSL.

---

### Post by jiansoco27 on 2023-06-28
Hi MAFoElffen,


Thanks a lot. I will follow your instructions. 


Appreciate both your guidance Bashing-om

---

### Post by Bashing-om on 2023-06-28
jiansoco27 -

Help is what we "try" to do >>

Let is know how this goes.

[INDENT]one of those times >>
[INDENT][INDENT]just no help for it
[/INDENT][/INDENT][/INDENT]

---

