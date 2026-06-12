---
title: "Fresh install of Lucid can't access repos"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by GhostC10 on 2011-01-26
For the better half of a week I've been trying to get a fresh install of Lucid running on my roomie's laptop. The apt-get update returns no errors and functions as normal. However, the apt-get upgrade command does this:

```

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  apparmor apparmor-utils erlang-base erlang-crypto erlang-inets erlang-mnesia
  erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools
  erlang-xmerl evolution evolution-common firefox firefox-branding
  firefox-gnome-support hpijs hplip hplip-data libapparmor-perl libapparmor1
  libhpmud0 libmagickcore2 libplymouth2 libpurple0 libwebkit-1.0-2
  linux-image-2.6.32-24-generic linux-libc-dev plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text plymouth-x11
33 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 64.8MB/79.9MB of archives.
After this operation, 459kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-24-generic 2.6.32-24.43
  Connection failed [IP: 91.189.88.31 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main linux-image-2.6.32-24-generic 2.6.32-24.43
  Connection failed [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main erlang-base 1:13.b.3-dfsg-2ubuntu2.1
  Connection failed [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main evolution 2.28.3-0ubuntu10.2
  Connection failed [IP: 91.189.92.169 80]
0% [Waiting for headers]

```However, if I do an apt-get install (package), anything that is in a non-core repo will be found. It won't be installed, because it attempts to install the above packages first.

My sources.list:

```

root@bekah-laptop:/home# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse

```I have searched many threads and tried many solutions. One thread mentioned using another mirror, but I can't figure out how to do that. I'd like to stick with Lucid if at all possible, but if the only solution is to upgrade to Maverick, so be it. I can provide more information if it would be helpful.

Edit: The school where I'm at (I have no other method of accessing the internet as of yet) put a pass-through system in place that has a remote server download and virus scan everything you attempt to download, than lets you d/l it from the server. That wouldn't cause the connections for fetching headers to fail, would it? It generally only uses this pass-through system on windows executables and .cmd files, though it's conceivable that the process of it checking might disrupt apt's normal activities.

---

### Post by BACbOK on 2011-01-26
> **GhostC10 said:**
> One thread mentioned using another mirror, but I can't figure out how to do that. I'd like to stick with Lucid if at all possible, but if the only solution is to upgrade to Maverick, so be it.
System --> Administration --> Source package --> main server :)[COLOR=blue][FONT=Arial][/FONT][/COLOR]

---

### Post by GhostC10 on 2011-01-26
Switched it from United States to Main Server. apt still hangs at

```

0% [Waiting for Headers]

```

and so on, same as the one in the first post.

Update Manager does the same, but displays less information.

---

### Post by GhostC10 on 2011-01-26
Some more error reports:

```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-28-generic_2.6.32-28.55_amd64.deb
  Connection failed [IP: 91.189.92.169 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-base_13.b.3-dfsg-2ubuntu2.1_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.28.3-0ubuntu10.2_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.28.3-0ubuntu10.2_all.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2_6.5.7.8-1ubuntu1.1_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.6-1ubuntu4.2_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.5-0ubuntu0.10.04.1_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.28.31_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.28.31_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-28_2.6.32-28.55_all.deb

```I am beginning to suspect that the problem is indeed the school's new network, which is very unfortunate because until I get paid, I have no internet at home. I would have if my phone hadn't been stolen... Such is life, I suppose.

---

### Post by GhostC10 on 2011-01-26
Solved. The school's network doesn't allow large downloads, including those done by Linux package managers. The Linux classes were congesting their networks. Awesome. I didn't need to install any software for said classes or anything.

---

