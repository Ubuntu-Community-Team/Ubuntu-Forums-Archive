---
title: "Upgrade from 11.10 beta to final, apt error"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by neon401 on 2011-11-23
I am trying to upgrade my Ubuntu 11.10 beta to final with the command:
```
sudo apt-get update
sudo do-release-upgrade -d
```

But it fails and gives me the following errors:

```
root@voltron:~# apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Get:1 http://archive.canonical.com oneiric Release.gpg [198 B]
Get:2 http://security.ubuntu.com oneiric-security Release.gpg [198 B]
Get:3 http://archive.canonical.com oneiric Release [5,922 B]
Get:4 http://security.ubuntu.com oneiric-security Release [32.4 kB]
Get:5 http://archive.canonical.com oneiric/partner Sources [1,848 B]
Get:6 http://archive.canonical.com oneiric/partner amd64 Packages [3,081 B]
Get:7 http://archive.canonical.com oneiric/partner i386 Packages [3,512 B]
Get:8 http://security.ubuntu.com oneiric-security/main Sources [17.1 kB]
Get:9 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]
Get:10 http://security.ubuntu.com oneiric-security/universe Sources [4,338 B]
Get:11 http://security.ubuntu.com oneiric-security/multiverse Sources [653 B]
Get:12 http://security.ubuntu.com oneiric-security/main amd64 Packages [45.8 kB]
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Get:13 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:14 http://security.ubuntu.com oneiric-security/universe amd64 Packages [14.1 kB]
Get:15 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [919 B]
Get:16 http://security.ubuntu.com oneiric-security/main i386 Packages [46.0 kB]
Get:17 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:18 http://security.ubuntu.com oneiric-security/universe i386 Packages [14.1 kB]
Get:19 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [1,653 B]
Get:20 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:21 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [71 B]
Get:22 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Ign http://no.archive.ubuntu.com oneiric InRelease
Ign http://no.archive.ubuntu.com oneiric-updates InRelease
Get:23 http://no.archive.ubuntu.com oneiric Release.gpg [198 B]
Get:24 http://no.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Get:25 http://no.archive.ubuntu.com oneiric Release [40.8 kB]
Get:26 http://no.archive.ubuntu.com oneiric-updates Release [32.4 kB]
Get:27 http://no.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:28 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Get:29 http://no.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Get:30 http://no.archive.ubuntu.com oneiric/universe Sources [4,677 kB]
Get:31 http://no.archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:32 http://no.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]
Get:33 http://no.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]
Get:34 http://no.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]
Get:35 http://no.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]
Get:36 http://no.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]
Get:37 http://no.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]
Get:38 http://no.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]
Get:39 http://no.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]
Get:40 http://no.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]
Get:41 http://no.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:42 http://no.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:43 http://no.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Get:44 http://no.archive.ubuntu.com oneiric-updates/main Sources [89.2 kB]
Get:45 http://no.archive.ubuntu.com oneiric-updates/restricted Sources [1,348 B]
Get:46 http://no.archive.ubuntu.com oneiric-updates/universe Sources [20.8 kB]
Get:47 http://no.archive.ubuntu.com oneiric-updates/multiverse Sources [1,992 B]
Get:48 http://no.archive.ubuntu.com oneiric-updates/main amd64 Packages [200 kB]
Get:49 http://no.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,966 B]
Get:50 http://no.archive.ubuntu.com oneiric-updates/universe amd64 Packages [53.6 kB]
Get:51 http://no.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [3,763 B]
Get:52 http://no.archive.ubuntu.com oneiric-updates/main i386 Packages [200 kB]
Get:53 http://no.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B]
Get:54 http://no.archive.ubuntu.com oneiric-updates/universe i386 Packages [54.1 kB]
Get:55 http://no.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,396 B]
Get:56 http://no.archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:57 http://no.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:58 http://no.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:59 http://no.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Fetched 18.2 MB in 4s (4,176 kB/s)
W: Failed to fetch copy:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index  Encountered a section with no Package: header

W: Failed to fetch copy:/var/lib/apt/lists/partial/no.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have googled for a fix and I see that most people solve this problem by removing the /var/lib/apt/lists directory. This did not work for me, however, so I was hoping someone knew of a different solution.

Thanks in advance.

---

### Post by LoderndenTech on 2011-11-23
Well im fairly new but from what I know there isn't a different release for each alpha, beta, and final you get updates automatically you don't have to do a release upgrade. So try "sudo apt-get update && sudo apt-get upgrade -f" without the "". The "-f" will fix any dependency problems which i had when I used the beta.

---

### Post by neon401 on 2011-11-23
> **LoderndenTech said:**
> Well im fairly new but from what I know there isn't a different release for each alpha, beta, and final you get updates automatically you don't have to do a release upgrade. So try "sudo apt-get update && sudo apt-get upgrade -f" without the "". The "-f" will fix any dependency problems which i had when I used the beta.
I would if I could. "apt-get update" gives me the error message I posted above.

---

### Post by LoderndenTech on 2011-11-23
Yah sorry i just realized that. "Note to self: Learn how to read"

---

### Post by neon401 on 2011-11-26
Sorry for bumping, but I'd really like to solve this issue.

---

### Post by dino99 on 2011-11-26
> **neon401 said:**
> Sorry for bumping, but I'd really like to solve this issue.

Really ? mixing i386 & amd64 is the fastest way to get troubles !!!
you need to do a choice: either 32 bits installation (i386) or 64 bits installation; which was before that mess ?

sudo gedit /etc/apt/sources.list

[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

---

### Post by neon401 on 2011-11-27
> **dino99 said:**
> Really ? mixing i386 & amd64 is the fastest way to get troubles !!!
you need to do a choice: either 32 bits installation (i386) or 64 bits installation; which was before that mess ?

sudo gedit /etc/apt/sources.list

[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)
First of all, I never changed the sources.list file at all. I figured it was downloading some i386 packages because there were no amd64 version of the package available.

Anyway, here's my sources.list
```

# 

# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted

# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

```
I can't find anything in there that says anything about amd64 or i386 (except for the cdrom source, which is commented out)

---

### Post by neon401 on 2011-12-01
Bump.

---

### Post by neon401 on 2011-12-06
Bump.

---

