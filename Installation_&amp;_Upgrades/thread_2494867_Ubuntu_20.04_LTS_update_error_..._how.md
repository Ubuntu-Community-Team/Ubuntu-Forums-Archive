---
title: "Ubuntu 20.04 LTS update error ... how ???"
date: 2024-01-29
forum: Installation &amp; Upgrades
---

### Post by l3modz on 2024-01-29
Hello, long time ago not see you all brothers, I'll wait Ubuntu next release LTS version, btw Ubuntu 20.04 of me got error...
```

root@pc-V-h81-intel-4570-desktop:~# apt-get update
Fetched 12,1 MB in 18s (677 kB/s)
Reading package lists... Done
N: Ignoring file 'maarten-fonville-ubuntu-android-studio-focal.list.save.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'maarten-fonville-ubuntu-android-studio-focal.list.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Skipping acquire of configured file 'multiverse/binary-i386/Packages' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/binary-amd64/Packages' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/i18n/Translation-en' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/i18n/Translation-en_US' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/Components-amd64.yml' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-48x48.tar' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-64x64.tar' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/cnf/Commands-amd64' as repository 'http://archive.canonical.com/ubuntu focal InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
root@pc-V-h81-intel-4570-desktop:~# 

```
enyone... how to fix it ??? delete the file error ??? it to risk.

But at Desktop Gnome login, and update, not get error, how fix this line.

---

### Post by deadflowr on 2024-01-29
Your source entries are wrong.
Change them from canonical to ubuntu

Yours show
```
'http://archive.**canonical**.com/ubuntu
```
should be
```
'http://archive.**ubuntu**.com/ubuntu
```

I don't think the canonical archive repo has anything other than Partner.
And Partner is basically obsolete, since the last useful package it provided was adobe-flashplugin.


EDIT:
You might post your sources.list file as you might already have the proper entry and only need to remove the referenced canonical entry(ies?)
Easiest to just copy the output from
```
cat /etc/apt/sources.list
```
and post it.

---

### Post by l3modz on 2024-01-29
> 
You said should be
```

'http://archive.ubuntu.com/ubuntu
```

and see at :
```
cat /etc/apt/sources.list

```

Well, I'll try.

---

### Post by l3modz on 2024-01-29
> **deadflowr said:**
> Your source entries are wrong.
Change them from canonical to ubuntu

EDIT:
You might post your sources.list file as you might already have the proper entry and only need to remove the referenced canonical entry(ies?)
Easiest to just copy the output from
```
cat /etc/apt/sources.list
```
and post it.

here it :
```

deb http://us.archive.ubuntu.com/ubuntu/ focal-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb http://download.virtualbox.org/virtualbox/debian focal contrib # disabled on upgrade to focal
# deb-src http://download.virtualbox.org/virtualbox/debian bionic contrib
deb http://archive.canonical.com/ubuntu focal multiverse
# deb-src http://archive.canonical.com/ubuntu bionic multiverse
deb http://archive.canonical.com/ focal partner
# deb-src http://archive.canonical.com/ bionic partner
# deb https://dl.winehq.org/wine-builts/ubuntu focal main # disabled on upgrade to focal
# deb-src https://dl.winehq.org/wine-builts/ubuntu bionic main
# deb https://deb.etcher.io stable etcher # disabled on upgrade to focal
# deb-src https://deb.etcher.io stable etcher


```

this was cat /etc/apt/sources.list of me.
nothin' special, not yet dream of Ubuntu Studio. ^_^ ^_^ ^_^

Soo I'll change **canonical** to **ubuntu.com**

---

### Post by l3modz on 2024-01-29
edit :
> 
EDIT:
You might post your sources.list file as you might already have the proper entry and only need to remove the referenced canonical entry(ies?)
Easiest to just copy the output from
```
cat /etc/apt/sources.list
```



> 
```

root@pc-V-h81-intel-4570-desktop:~# apt-get update
...
...
...
Hit:11 http://us.archive.ubuntu.com/ubuntu focal-security InRelease
Get:12 http://archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal/multiverse i386 Packages [74,7 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal/multiverse amd64 DEP-11 Metadata [48,4 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal/multiverse DEP-11 48x48 Icons [23,1 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal/multiverse DEP-11 64x64 Icons [192 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9.136 B]
Err:19 http://archive.ubuntu.com focal Release
  404  Not Found [IP: 91.189.xx.xx xx]

** (appstreamcli:6903): WARNING **: 03:16:13.722: No origin found for file us.archive.ubuntu.com_ubuntu_dists_focal_universe_dep11_Components-amd64.yml.gz

** (appstreamcli:6903): WARNING **: 03:16:13.723: No origin found for file us.archive.ubuntu.com_ubuntu_dists_focal_multiverse_dep11_Components-amd64.yml.gz
Reading package lists... Done
E: The repository 'http://archive.ubuntu.com focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
root@pc-V-h81-intel-4570-desktop:~#

```


---

### Post by l3modz on 2024-01-29
The conclusion was :
The repository 'http://archive.ubuntu.com focal Release' does not have a Release file.

> 
```
E: The repository 'http://archive.ubuntu.com focal Release' does not have a Release file.

```


But alwasy success update using Desktop Version, Gnome Version : Software Updater. 
Using Terminal console, yup, it : **E: The repository 'http://archive.ubuntu.com focal Release' does not have a Release file.**

---

### Post by MAFoElffen on 2024-01-30
You never posted the output showing the contents of your changed sources.list file to confirm it was good... In that case, how about this.

What happens if you try this as your /etc/apt/sources.list file?
```

deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted universe multiverse

```

---

