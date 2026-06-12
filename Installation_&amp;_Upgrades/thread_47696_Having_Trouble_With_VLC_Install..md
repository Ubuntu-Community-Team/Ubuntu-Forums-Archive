---
title: "Having Trouble With VLC Install."
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by Cerbz on 2005-07-09
I go to install VLC with synaptic, it tries to retrieve the files, but at the end i get this error message and it asks me something... i pressed no..

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/wxvlc_0.8.1-1ubuntu7_i386.deb)
  MD5Sum mismatch



Any idea of whats going on? some help would be much appreciated!! thanks guys.

---

### Post by Lord Illidan on 2005-07-09
You probably have to change the location of the repository..Try changing the locations in /etc/apt/sources.list to uk, instead of us.
Remember to back up the sources.list, and you need sudo access to do it..

sudo cp /etc/apt/sources.list /etc/apt/sources.backup
sudo vi /etc/apt/sources.list

Voila`!

---

### Post by Cerbz on 2005-07-09
[QUOTE=Lord Illidan]You probably have to change the location of the repository..Try changing the locations in /etc/apt/sources.list to uk, instead of us.
Remember to back up the sources.list, and you need sudo access to do it..

sudo cp /etc/apt/sources.list /etc/apt/sources.backup
sudo vi /etc/apt/sources.list

Voila`![/QUOTE]


How do i change it to the UK?? what do i put?

---

### Post by terrien on 2005-07-09
Wow, I have no idea what happened to the US repositories, but changing your sources.list file to look like this:

```

# deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

might help.. note the removal of the country extensions, which might be faster for you if you live in the US.... then make sure to run

sudo apt-get update

afterwards.

---

