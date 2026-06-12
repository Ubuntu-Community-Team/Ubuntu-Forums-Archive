---
title: "Trouble updating. Failed connecting to default and official repository. Fresh 6.06LTS"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by sogreenithurts on 2007-04-11
Hello folks. Thanks for your help in advance. I just installed Ubuntu 6.06 LTS (Dapper Drake) Desktop (not Server) from the DVD i386 ISO download I burned to disc. I can access the Internet just fine with Firefox 1.5.0.3. Now the little update icon in the top right corcer tells me there are updates.

Problem is, every time I try to apply the updates it fails. Upon closer inspection, I can see the "Status" colum to the left of the "URI" column under the "Show progress of single files" option is "Failed" for every one. What should I do now? I'm kinda stuck and I'd like to apply the updates. Thanks for your help. Other than this, everything else seems to be working just fine. :)

---

### Post by zvacet on 2007-04-11
Do you have all repositories open?
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Programs>accessories>terminal

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by sogreenithurts on 2007-04-11
I have checked off all "officially supported" repositories in the "Software Preferences" dialog. I did so when I first asked the question earlier today. However, it still doesn't update. I have a fresh ubuntu install. I've installed no other software and configured nothing else since the OS install.

Shouldn't ubuntu update right out of the box? Specially since my network connection and Internet access work? Do you think I should apply the terminal command given? If you say so I will, but I don't want to botch something else up trying to fix this. Yep. I'm so green, it hurts. Thanks for your help.

---

### Post by sogreenithurts on 2007-04-20
It has been a week and I'm still stumped. I can't update my Ubuntu Linux installation. Will anybody help? Please?

---

### Post by sogreenithurts on 2007-04-20
For anyone who might be able to help me here is more information. I ventured into the Terminal, typed in "sudo apt-get update", hit enter, entered my password, and this is what I get as a result. I still don't know what to do.

> ubuser@ubu:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 130.239.18.41 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 130.239.18.159 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 130.239.18.158 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 130.239.18.159 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 130.239.18.158 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 130.239.18.41 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 130.239.18.159 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 130.239.18.158 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 130.239.18.41 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 130.239.18.159 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 130.239.18.158 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 130.239.18.41 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 130.239.18.159 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 130.239.18.158 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 130.239.18.41 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 130.239.18.159 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 130.239.18.158 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 130.239.18.41 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 130.239.18.41 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Connection failed [IP: 130.239.18.158 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.158 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 130.239.18.41 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.158 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.41 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 130.239.18.158 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.41 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.158 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 130.239.18.41 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz)  Connection failed [IP: 130.239.18.159 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Connection failed [IP: 130.239.18.158 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Connection failed [IP: 130.239.18.41 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Connection failed [IP: 130.239.18.159 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuser@ubu:~$


---

### Post by sogreenithurts on 2007-04-21
I'm a bit frustrated by the fact my request has gotten no response. :-( Anyhow, I've been doing my best to try and fix the problem. I downloaded 6.06.1 LTS a few hours ago and reinstalled from scratch thinking the .1 update may have helped. Unfortunately, it did not. My initial install was using a CD I'd created using the the ISO from July of last year.

Here's a few Software Preferences screenshots for whoever is interested in helping out.

[CENTER][IMG]http://i169.photobucket.com/albums/u210/sogreenithurts/2007_04_21SoftwarePreferencesWindow.gif[/IMG]

[IMG]http://i169.photobucket.com/albums/u210/sogreenithurts/2007_04_21SoftwarePreferencesWin-1.gif[/IMG]

[IMG]http://i169.photobucket.com/albums/u210/sogreenithurts/2007_04_21SoftwarePreferencesWin-3.gif[/IMG]

[IMG]http://i169.photobucket.com/albums/u210/sogreenithurts/2007_04_21SoftwarePreferencesWin-2.gif[/IMG][/CENTER]

And finally, here is more information from the command line (copied and pasted from the Terminal):
> ubuser@ubu:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  app-install-data-commercial cpio dpkg dselect evolution-data-server hal hal-device-manager language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libc6 libc6-i686 libcamel1.2-8 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7
  libedataserverui1.2-6 libegroupwise1.2-9 libexchange-storage1.2-1 libhal-storage1 libhal1 libspeex1 locales lvm2 synaptic xserver-xorg-core
29 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.7MB of archives.
After unpacking 12.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  dpkg locales libc6 libc6-i686 lvm2 language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base cpio dselect
  app-install-data-commercial libedataserver1.2-7 libegroupwise1.2-9 libcamel1.2-8 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  evolution-data-server libhal1 hal hal-device-manager libedataserverui1.2-6 libexchange-storage1.2-1 libhal-storage1 libspeex1 synaptic xserver-xorg-core
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main dpkg 1.13.11ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main locales 2.3.18.3
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libc6 2.3.6-0ubuntu20.4
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libc6-i686 2.3.6-0ubuntu20.4
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main lvm2 2.02.02-1ubuntu1.5
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main language-pack-en 1:6.06+20070129
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main language-pack-en-base 1:6.06+20070129
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main language-pack-gnome-en 1:6.06+20070311
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main language-pack-gnome-en-base 1:6.06+20070129
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main cpio 2.6-10ubuntu0.2
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main dselect 1.13.11ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main app-install-data-commercial 5.5
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libedataserver1.2-7 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libegroupwise1.2-9 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libcamel1.2-8 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libebook1.2-5 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libecal1.2-3 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libedata-book1.2-2 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libedata-cal1.2-1 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main evolution-data-server 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libhal1 0.5.7-1ubuntu18.2
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main hal 0.5.7-1ubuntu18.2
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main hal-device-manager 0.5.7-1ubuntu18.2
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libedataserverui1.2-6 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libexchange-storage1.2-1 1.6.1-0ubuntu7
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libhal-storage1 0.5.7-1ubuntu18.2
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libspeex1 1.1.11.1-1ubuntu0.2
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main synaptic 0.57.8ubuntu13
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main xserver-xorg-core 1:1.0.2-0ubuntu10.4
  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.3_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.6-0ubuntu20.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.6-0ubuntu20.4_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.6-0ubuntu20.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.6-0ubuntu20.4_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1.5_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20070129_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20070129_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20070129_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20070129_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20070311_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20070311_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_6.06+20070129_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_6.06+20070129_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10ubuntu0.2_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_5.5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_5.5_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-7_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-9_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-9_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-8_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-8_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-5_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-5_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-3_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-3_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-1_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-1_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-6_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-6_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-1_1.6.1-0ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-1_1.6.1-0ubuntu7_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.11.1-1ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.11.1-1ubuntu0.2_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.8ubuntu13_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.8ubuntu13_i386.deb)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuser@ubu:~$


---

### Post by DougieFresh4U on 2007-04-21
How about changing that "us" in your sources list to another country code, I use "gb" as I have had good luck and speed with that one. Also when you do **sudo apt-get update** then **sudo apt-get dist-upgrade** I will assume you are going up to Edgy Maybe you might want to uncomment repo's while your in that sources list

---

### Post by sogreenithurts on 2007-04-21
Thanks for replying.

I'd like to stick with the LTS distribution if at all possible. I'm evaluating the distro for other possible installs on work machines. But as you can tell, I'm a newbie at this.

What country is "gb"? And how do I go about changing "us" to "gb" without manually editing every line?

Why can't I update from a default, fresh installation?

---

### Post by pnix on 2007-04-22
I guess gb is "great britain". I use Dapper LTS desktop for a long time with out any problem(with "th" mirror). I agree with DougieFresh4U that you should try change to update from other country mirror.

---

### Post by sogreenithurts on 2007-04-24
Why is the US repository not working for me? Again, this is a fresh install. I've changed no default settings except to answer questions the system asked me. I chose the "New York" time zone while installing as I am in the East Coast of the United States. Is anyone or everyone else in the US having this problem?

---

### Post by rpaco on 2007-04-27
Hi sorry this is not a solution, just to say I have the same problems I cannot update by any means the command line method sudo apt update etc gets the same failed message on all the files it tries to get. My update repository codes are all set to gb so that does not help at all. I get the same problem if I try and use the synaptic package manager as well  Also my Evolution email cannot connect although Firefox is connected. I had to use "blacklist ivp6" in set/modprobe.d/blacklist  in order to get Firefox to connect. I was hoping Chilli555 would read this and come up with a solution since he solved my Firefox connection problem.

---

### Post by sogreenithurts on 2007-05-03
Does anyone know of any other good web sites on the Internet where I can go to get my questions answered? Getting help through this forum takes too long. While I appreciate people's responses so far, they haven't really helped get me any closer to answering my initial questions.

---

### Post by sogreenithurts on 2007-05-03
Does anyone know of any other good web sites on the Internet where I can go to get my questions answered? Getting help through this forum takes too long. While I appreciate people's responses so far, they haven't really helped get me any closer to answering my initial questions.

---

### Post by sogreenithurts on 2007-05-09
Well, I first posted about my problem 4 weeks ago. I believe I've waited long enough. A heartfelt thank you goes out to those to took time out of their day to reply and try and help.

I'll keep looking around for other Ubuntu LTS support options. One thing is for sure, support isn't there for small business. This is where Microsoft Windows and Apple Mac OS X definitely come in as real options in the business world.

Thanks. And goodbye for now.

---

### Post by Najand on 2007-05-09
Are you behind a proxy server or a router?

---

