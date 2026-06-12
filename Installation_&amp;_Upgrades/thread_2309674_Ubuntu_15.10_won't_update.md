---
title: "Ubuntu 15.10 won't update"
date: 2016-01-12
forum: Installation &amp; Upgrades
---

### Post by Godolphinhill on 2016-01-12
I'm a newcomer to all this so please bear with me. I've installed Ubuntu 15.10 on my lenovo T410 which already had Windows 10 installed. I used the official DVD. Unfortunately I cannot update the software or download any more. When I try using the updater it returns:

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f
.

I then did this and the result was an error code 1

I'm mystified and will be grateful for help.

---

### Post by Bashing-om on 2016-01-12
Godolphinhill; Hello;

Looks to be a conflict in internet messaging accounts .
Pictures are difficult to work from .. please post back - Between Code Tags - the complete outputs of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So we know what you have and then are able to make a determination of what we are working toward .

[INDENT][INDENT]what does it take 
[INDENT][INDENT][INDENT]to keep a package manager
[INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Godolphinhill on 2016-01-13
Thanks for getting back to me. I tried do what you asked but it seems impossible to highlight and copy from the terminal. How do I do this please?
Thanks


> **Bashing-om said:**
> Godolphinhill; Hello;

Looks to be a conflict in internet messaging accounts .
Pictures are difficult to work from .. please post back - Between Code Tags - the complete outputs of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So we know what you have and then are able to make a determination of what we are working toward .
[INDENT][INDENT]what does it take [INDENT][INDENT][INDENT]to keep a package manager[INDENT][INDENT][INDENT]satisfied


[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Godolphinhill on 2016-01-13
> **Godolphinhill said:**
> I'm a newcomer to all this so please bear with me. I've installed Ubuntu 15.10 on my lenovo T410 which already had Windows 10 installed. I used the official DVD. Unfortunately I cannot update the software or download any more. When I try using the updater it returns:

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f
.

I then did this and the result was an error code 1

I'm mystified and will be grateful for help.

The output requested is:

```
john@john-ThinkPad-T410:~$ sudo apt update
[sudo] password for john: 
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily InRelease
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily Release.gpg
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily Release
Err cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/main Translation-en_GB
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/main Translation-en
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/restricted Translation-en_GB
Ign cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021) wily/restricted Translation-en
Hit http://archive.canonical.com wily InRelease                                
Hit http://gb.archive.ubuntu.com wily InRelease                                
Get:1 http://gb.archive.ubuntu.com wily-updates InRelease [64.4 kB]            
Get:2 http://security.ubuntu.com wily-security InRelease [64.4 kB]             
Hit http://archive.canonical.com wily/partner Sources                          
Hit http://archive.canonical.com wily/partner amd64 Packages                   
Hit http://archive.canonical.com wily/partner i386 Packages                    
Hit http://archive.canonical.com wily/partner Translation-en                   
Get:3 http://security.ubuntu.com wily-security/main Sources [26.0 kB]
Get:4 http://security.ubuntu.com wily-security/universe Sources [7,013 B]
Get:5 http://security.ubuntu.com wily-security/multiverse Sources [1,913 B]
Get:6 http://security.ubuntu.com wily-security/main amd64 Packages [80.5 kB]
Get:7 http://gb.archive.ubuntu.com wily-updates/main Sources [41.9 kB]
Get:8 http://gb.archive.ubuntu.com wily-updates/universe Sources [11.7 kB]     
Get:9 http://gb.archive.ubuntu.com wily-updates/multiverse Sources [1,913 B]
Get:10 http://security.ubuntu.com wily-security/universe amd64 Packages [36.5 kB]
Get:11 http://gb.archive.ubuntu.com wily-updates/main amd64 Packages [112 kB]
Get:12 http://security.ubuntu.com wily-security/multiverse amd64 Packages [5,856 B]
Get:13 http://gb.archive.ubuntu.com wily-updates/universe amd64 Packages [51.1 kB]
Get:14 http://security.ubuntu.com wily-security/main i386 Packages [78.5 kB]
Get:15 http://security.ubuntu.com wily-security/universe i386 Packages [36.5 kB]
Get:16 http://gb.archive.ubuntu.com wily-updates/multiverse amd64 Packages [5,856 B]
Get:17 http://security.ubuntu.com wily-security/multiverse i386 Packages [6,064 B]
Get:18 http://gb.archive.ubuntu.com wily-updates/main i386 Packages [109 kB]
Get:19 http://security.ubuntu.com wily-security/main Translation-en [40.4 kB]
Get:20 http://security.ubuntu.com wily-security/multiverse Translation-en [2,536 B]
Get:21 http://security.ubuntu.com wily-security/universe Translation-en [24.1 kB]
Get:22 http://gb.archive.ubuntu.com wily-updates/universe i386 Packages [49.2 kB]
Get:23 http://gb.archive.ubuntu.com wily-updates/multiverse i386 Packages [6,064 B]
Get:24 http://gb.archive.ubuntu.com wily-updates/main Translation-en [54.9 kB]
Get:25 http://gb.archive.ubuntu.com wily-updates/multiverse Translation-en [2,536 B]
Get:26 http://gb.archive.ubuntu.com wily-updates/universe Translation-en [32.8 kB]
Hit http://gb.archive.ubuntu.com wily/main Sources      
Hit http://gb.archive.ubuntu.com wily/universe Sources
Hit http://gb.archive.ubuntu.com wily/multiverse Sources
Hit http://gb.archive.ubuntu.com wily/main amd64 Packages
Hit http://gb.archive.ubuntu.com wily/universe amd64 Packages
Hit http://gb.archive.ubuntu.com wily/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com wily/main i386 Packages
Hit http://gb.archive.ubuntu.com wily/universe i386 Packages
Hit http://gb.archive.ubuntu.com wily/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com wily/main Translation-en_GB
Hit http://gb.archive.ubuntu.com wily/main Translation-en
Hit http://gb.archive.ubuntu.com wily/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com wily/multiverse Translation-en
Hit http://gb.archive.ubuntu.com wily/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com wily/universe Translation-en
Fetched 954 kB in 9s (98.9 kB/s)                                               
W: Failed to fetch cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)/dists/wily/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)/dists/wily/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)/dists/wily/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)/dists/wily/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
john@john-ThinkPad-T410:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
E: Unmet dependencies. Try using -f.
john@john-ThinkPad-T410:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libasound2:i386 libatk1.0-0:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libcairo2:i386 libcups2:i386
  libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386 libexpat1:i386
  libffi6:i386 libfontconfig1:i386 libfreetype6:i386 libgconf-2-4:i386
  libgdk-pixbuf2.0-0:i386 libglib2.0-0:i386 libgmp10:i386
  libgnome-keyring0:i386 libgnutls-deb0-28:i386 libgraphite2-3:i386
  libgssapi-krb5-2:i386 libgtk2.0-0:i386 libharfbuzz0b:i386 libhogweed4:i386
  libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 libnettle6:i386
  libnspr4:i386 libnss3:i386 libp11-kit0:i386 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpixman-1-0:i386
  libpng12-0:i386 libsqlite3-0:i386 libstdc++6:i386 libtasn1-6:i386
  libthai0:i386 libtiff5:i386 libx11-6:i386 libxau6:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386
  libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxss1:i386
  libxtst6:i386 thunderbird-locale-en thunderbird-locale-en-gb
  thunderbird-locale-en-us
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed
  kde-config-telepathy-accounts
0 to upgrade, 1 to newly install, 0 to remove and 69 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/138 kB of archives.
After this operation, 828 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 273837 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.10.20150723-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks

---

### Post by Bashing-om on 2016-01-13
Godolphinhill; Yeah ...

Much easier to work with this when outputs are within text code tags.
So, we have 2 issues.
1) Is that the CD source is enabled in your Ubuntu Software Center -> software sources; uncheck the source.

2) Yeah we do have a conflict in internet messaging clients ... :
> 
The following packages have unmet dependencies.
kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0)

bk

dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.10.201


Which do you prefer ? We remove the other .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Godolphinhill on 2016-01-13
Sorry. I don't understand your 2nd point.

---

### Post by Bashing-om on 2016-01-13
Godolphinhill; Well ...

The way I read the error advisory you may not install both
kde-config-telepathy
google-im.service

so choose which one you desire to have on your system ( or none at all for that matter ) .

[INDENT][INDENT]like the lawyers say
[INDENT][INDENT][INDENT]a conflict of interest
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Godolphinhill on 2016-01-13
Bashing-Om
Thanks for your help. As far as I know I didn't try to install either of those things. I'll have to try to find out how to stop them both.
Thanks again

---

### Post by Bashing-om on 2016-01-13
Godolphinhill; Well ...

as to Google .. 3rd party software ... Probably installed as a dependency of something else Google.
Let's look and see what you installed:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Depending on what is and what you want is what we do.

[INDENT]a means to an end
[/INDENT]

---

