---
title: "Trusty stuck at point-release version 14.04.4"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by Cbhihe on 2016-08-26
*This is **NOT** a question about going from Ubuntu Desktop LTS 14.04 to 16.04*, rather one about why I'm stuck at point-release 14.04.4 and unable to go on to 14.04.5.

For reference:
         ```
[FONT=courier new]
$ uname -a
Linux HOSTNAME 3.16.0-50-generic #67~14.04.1-Ubuntu SMP
Fri Oct 2 22:07:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a | grep -i descript
Description:    Ubuntu 14.04.4 LTS[/FONT]

```
I have unattended updates set up for:

[LIST]
[*]Important security updates (trusty-security) 
[*]Recommended updates (trusty-updates) 
[*]Unsupported updates (trusty-backports) 
[/LIST]
  "trusty-proposed" is off.

Even when running 
         ```
[FONT=courier new]$ sudo apt-get update
$ sudo apt-get -y upgrade
$ sudo apt-get dist-upgrade [/FONT]
```
I remain stuck at 14.04.4, the 2016-02-18 Trusty point-release.

I have searched AU and found [this]("https://askubuntu.com/questions/808529/how-to-upgrade-from-14-04-4-to-14-04-5") on the 14.04.4 to 14.04.5 `dist-upgrade` front. It did not help.
 
I may have a configuration issue that escapes me or I may be confusing upgrades and updates, version and release or my kernel version is out of whack... 
Suggestions much welcome.

---

### Post by grahammechanical on 2016-08-26
Try this command

```
lsb_release -a
```

The uname -a command shows the kernel version but you may be at the 14.04.5 release but to get the 14.04.5 kernel you may need to upgrade the hardware enablement stack.

> In an effort to support a wider variety of hardware on an existing LTS  release, the 14.04.5 point release will ship with an updated kernel and X  stack by default. This newer hardware enablement stack will be  comprised of the kernel and X stack from the Xenial 16.04 release.

> Anyone wishing to opt into the hardware enablement  stack for Trusty may do so by running following command which will  install the linux-generic-lts-xenial and xserver-xorg-lts-xenial  packages: 


 sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial  


If you are on an amd64 system that boots with UEFI, you will also need the matching signed kernel: 

 sudo apt-get install linux-signed-generic-lts-xenial 



[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

Regards

---

### Post by Cbhihe on 2016-08-26
Thank you @Grahammechanical.
Output of [FONT=courier new]lsb_release[/FONT] is already in OP. I do have the 14.04.4 point release.
I have read 100% of the release notes per yr link. Interesting.
I will explore the HWE stack route over the weekend and report here... 
Need to do a full backup first. Never know. More later.
Cheers,
-ced

---

### Post by kansasnoob on 2016-08-26
Post the full output of:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Clearly something is amiss. Once we get you fully updated the update-manager will notify you of the HWE upgrade.

---

### Post by Cbhihe on 2016-08-27
Hello Kansasnoob, 
Thank you and here are 2 outputs as requested. 
Sorry I must display the first one here in extenso, but for some weird reason
this platform does not let me add an attachment.

```
$  sudo apt-get update | tee update.log
Ign file:  InRelease
Get:1 file:  Release.gpg [198 B]
Get:2 file:  Release [196 B]
Ign file:  Translation-en_US
Ign file:  Translation-en
Ign file:  Translation-en_AU
Ign file:  Translation-en_CA
Ign file:  Translation-en_GB
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty Release.gpg
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty Release
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main Sources
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main Translation-en_CA
Hit [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main Translation-en_GB
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_AU
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_CA
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_AU
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_CA
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main Translation-en_US
Ign [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted Translation-en
Ign [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main Translation-en_AU
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted Translation-en_AU
Ign [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main Translation-en_CA
Ign [http://apt.postgresql.org](http://apt.postgresql.org) trusty-pgdg/main Translation-en_GB
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted Translation-en_GB
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe Translation-en_AU
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe Translation-en_CA
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe Translation-en_GB
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates Release.gpg
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security Release.gpg
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports Release.gpg
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates Release
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security Release
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports Release
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main amd64 Packages
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main i386 Packages
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_US
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_AU
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_CA
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_GB
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/main Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/restricted Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/universe Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/multiverse Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/main amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/restricted amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/universe amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/multiverse amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/main i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/restricted i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/universe i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/multiverse i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/main Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/multiverse Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/restricted Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-updates/universe Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/main Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/restricted Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/universe Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/multiverse Sources
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/main amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/restricted amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/universe amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/multiverse amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/main i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/restricted i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/universe i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/multiverse i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/main Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/multiverse Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/restricted Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-security/universe Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/main amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/universe amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/multiverse amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/restricted amd64 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/main i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/universe i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/multiverse i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/restricted i386 Packages
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/main Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/multiverse Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/restricted Translation-en
Hit [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty-backports/universe Translation-en
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/main Translation-en_US
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse Translation-en_US
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/multiverse Translation-en_CA
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted Translation-en_US
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/restricted Translation-en_CA
Ign [http://sunsite.rediris.es](http://sunsite.rediris.es) trusty/universe Translation-en_US
Reading package lists...
```

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by Bucky Ball on 2016-08-27
Please use code tags. I have added them to your last post to avoid confusion. Makes it easier to read. See the link in my signature for how to create them. 

You can add attachments by clicking 'Go Advanced' or 'Adv Reply' and use the paperclip icon there to add attachments.

---

### Post by Cbhihe on 2016-08-27
Bucky Ball, 
Formatting is always better, but I have issues  navigating UF and am currently troubleshooting. Clicking on anything that sends me  to another page or reloads it,  automatically disconnects me. "Go  advanced" is one of those things. So while I am troubleshooting (it may  be a simple cookie problem, but I am not certain yet) I thought I'd make do. See [my  post]("https://ubuntuforums.org/showthread.php?t=2335274") in "Forum Feedback & Help"
Thanks for the heads-up.
-ced

---

### Post by Bucky Ball on 2016-08-27
> **Cbhihe said:**
> Bucky Ball, 
Formatting is always better, but I have issues  navigating UF and am currently troubleshooting. Clicking on anything that sends me  to another page or reloads it,  automatically disconnects me. "Go  advanced" is one of those things. So while I am troubleshooting (it may  be a simple cookie problem, but I am not certain yet) I thought I'd make do. See [my  post]("https://ubuntuforums.org/showthread.php?t=2335274") in "Forum Feedback & Help"
Thanks for the heads-up.
-ced

Roger that. :)

---

### Post by howefield on 2016-08-27
Could be the mirror that you are using, perhaps try changing to the main archives/server.

---

### Post by Cbhihe on 2016-08-28
@howefield:
I sincerely doubt that [http://sunsite.rediris.es](http://sunsite.rediris.es)   is to blame. I did try a handful of other sites in my geographical  area  and sunsite.rediris.es gives me the best results, others in  Germany or  England for instance used to give me "missing package - old  package will  be retained" messages when updating (wording is  approximate). 
@Grahammechanical's HWE based suggestion has not raised an outcry in UF  yet (  :-P ); it strikes me as reasonable and it is documented. If it  does not work then I will explore more site-wise per yr suggestion... 
Cheers,
-ced.

---

### Post by atrab101 on 2016-08-29
> **kansasnoob said:**
> Post the full output of:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Clearly something is amiss. Once we get you fully updated the update-manager will notify you of the HWE upgrade.

Definitely agree.  The below was my experience.  Question would be why didn't normal updating get to the 14.04.5 version with subsequent warning?

I had been doing all updates since installing 14.04.4 in February 2016.  My system indicated the 14.04.05 version as of early August, but my system was still at the 4.2.0 -42 kernel and associated HWE stack.  An upgrade of the HWE stack is not intended to happen automatically.  Then I received the security warning that I was no longer getting security updates to that kernel.  I upgraded the HWE stack and it took me to new kernel 4.4.0 -34 with support to April 2019.  Everything works great.

Regards

---

### Post by Cbhihe on 2016-09-08
> **grahammechanical said:**
> Try this command

```
lsb_release -a
```

The uname -a command shows the kernel version but you may be at the 14.04.5 release but to get the 14.04.5 kernel you may need to upgrade the hardware enablement stack.





[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

Regards

I tried:
```
$ sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial
[sudo] password for USER:_____ 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-lts-xenial
E: Unable to locate package xserver-xorg-core-lts-xenial
E: Unable to locate package xserver-xorg-lts-xenial
E: Unable to locate package xserver-xorg-video-all-lts-xenial
E: Unable to locate package xserver-xorg-input-all-lts-xenial
E: Unable to locate package libwayland-egl1-mesa-lts-xenial
```

That's new to me. Any suggestion ?

---

### Post by brian-murray on 2016-09-13
It certainly looks like the mirror to me, if you look at [http://sunsite.rediris.es/mirror/ubuntu-archive/](http://sunsite.rediris.es/mirror/ubuntu-archive/) you see messages that an archive update is in progress from September 2015.

Also the most recent version of update-manager, which I've uploaded within the past month for Trusty, doesn't exist here.

[http://sunsite.rediris.es/mirror/ubuntu-archive/pool/main/u/update-manager/](http://sunsite.rediris.es/mirror/ubuntu-archive/pool/main/u/update-manager/)

I strongly encourage you to switch mirrors as you are not getting security updates either.  You can find an official list of mirrors here:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Cbhihe on 2016-09-14
@howefield and @brian-murray:
In the end you were both right.

I chose a mirror in the US. 
As soon as I finished updating my DB, bingo. 
I  immediately got notification about 350 (yessir!) pending upgrades among  them quite a few security upgrades dating back to up to a little more  than a year. 

As I write I am waiting for the `sudo apt-get  upgrade` process to complete, before I go on to sudo apt-get  dist-upgrade` and graduate to point version 14.04.5 with kernel 4.x.

I now close this thread as solved. Again thanks all. 

-ced

---

### Post by howefield on 2016-09-14
Thanks for the update, hope the rest of the update goes well :)

---

