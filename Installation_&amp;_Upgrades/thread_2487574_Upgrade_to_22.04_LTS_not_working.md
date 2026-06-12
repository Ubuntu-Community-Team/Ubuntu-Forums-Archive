---
title: "Upgrade to 22.04 LTS not working"
date: 2023-06-08
forum: Installation &amp; Upgrades
---

### Post by lawrence-joy on 2023-06-08
Here are the terminal commands I have done and the results:
larry@larry-MS-7693:~$ sudo apt update
[sudo] password for larry: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB] 
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]     
Hit:4 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) focal InRelease                     
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]             
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [2,613 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [59.8 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [95.4 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [940 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [274 kB]                                                                                                                      
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [731 kB]                                                                                                                          
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [1,070 kB]                                                                                                                       
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [410 kB]                                                                                                                  
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [944 B]                                                                                                                 
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/main amd64 DEP-11 Metadata [8,004 B]                                                                                                                   
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [30.5 kB]                                                                                                               
Fetched 5,630 kB in 13s (439 kB/s)                                                                                                                                                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
larry@larry-MS-7693:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libavformat58 librpmsign8 python2.7-dbg libmagick++-6.q16-8 libavfilter7
  rpm2cpio ffmpeg graphviz-doc libmagickcore-6.q16-6-extra imagemagick
  libswresample3 libgegl-0.4-0 ant librpmbuild8 libzmq5 python2.7-minimal
  libmagickwand-6.q16-6 libgegl-common libcgraph6 libpython2.7 debugedit
  python2.7 libpython2.7-dbg python3-rpm libpostproc55 liblab-gamut1 librpmio8
  imagemagick-6.q16 rpm-common rpm-i18n rpm librpm8 libnetty-java libavcodec58
  libpostgresql-jdbc-java libjs-jquery-ui libcdt5 libavutil56 libpathplan4
  libavdevice58 libhttpclient-java libswscale5 libgvpr2 libopenexr24
  libsdl2-2.0-0 libmysofa1 libmagickcore-6.q16-6 ant-doc libpython2.7-minimal
  ffmpeg-doc libgvc6 libpython2.7-stdlib graphviz ant-optional libavresample4
  imagemagick-6-common
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages have been kept back:
  mesa-opencl-icd
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
larry@larry-MS-7693:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
larry@larry-MS-7693:~$ sudo snap refresh
gnome-42-2204 0+git.587e965 from Canonical&#10003; refreshed
larry@larry-MS-7693:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal
larry@larry-MS-7693:~$ do-release-upgrade -d
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
***I thought I did by entering the 'sudo apt upgrade command'. What is going on? How do I accomplish the upgrade?

---

### Post by Bashing-om on 2023-06-08
lawrence-joy Hey hey

"do-release-upgrade [color=red]-d[/color]"
that -d switch is development version - as 22.04 is no longer in development - try as:
```

sudo apt update
sudo apt upgrade
sudo do-release-upgrade

```

[INDENT]my bit to try and help
[/INDENT]

---

### Post by ne29914 on 2023-06-08
Also, sudo is missing on the last commands...

---

### Post by lawrence-joy on 2023-10-04
I did as you stated dropping the -d and still get the same message:
larry@larry-MS-7693:~$ sudo do-release-upgrade
[sudo] password for larry: 
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

larry@larry-MS-7693:~$ sudo apt update
[sudo] password for larry: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease                                         
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease                                       
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Hit:5 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) focal InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
larry@larry-MS-7693:~$ apt list --upgradable
Listing... Done
mesa-opencl-icd/focal-updates,focal-security 21.2.6-0ubuntu0.1~20.04.2 amd64 [upgradable from: 21.0.3-0ubuntu0.3~20.04.4]
N: There are 2 additional versions. Please use the '-a' switch to see them.
larry@larry-MS-7693:~$ apt list --upgradable -a
Listing... Done
mesa-opencl-icd/focal-updates,focal-security 21.2.6-0ubuntu0.1~20.04.2 amd64 [upgradable from: 21.0.3-0ubuntu0.3~20.04.4]
mesa-opencl-icd/now 21.0.3-0ubuntu0.3~20.04.4 amd64 [installed,upgradable to: 21.2.6-0ubuntu0.1~20.04.2]
mesa-opencl-icd/focal 20.0.4-2ubuntu1 amd64
>>Apparently there is this one package to upgrade but I do not know how or what to do. So I executed the upgrade command.

larry@larry-MS-7693:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-bin vlc-plugin-video-output libavformat58 librpmsign8 python2.7-dbg
  libmagick++-6.q16-8 libavfilter7 rpm2cpio ffmpeg vlc-plugin-samba
  graphviz-doc libmagickcore-6.q16-6-extra imagemagick libswresample3
  vlc-plugin-qt libgegl-0.4-0 ant librpmbuild8 libzmq5 python2.7-minimal
  libmagickwand-6.q16-6 vlc-plugin-skins2 libgegl-common
  vlc-plugin-visualization vlc-l10n libcgraph6 libpython2.7 debugedit
  python2.7 vlc-plugin-notify libvlc5 libpython2.7-dbg python3-rpm
  libpostproc55 liblab-gamut1 libvlccore9 libvlc-bin librpmio8
  imagemagick-6.q16 rpm-common rpm-i18n libgsasl7 rpm librpm8 libnetty-java
  libavcodec58 libpostgresql-jdbc-java libjs-jquery-ui vlc libcdt5 libavutil56
  vlc-data libpathplan4 libavdevice58 libhttpclient-java libswscale5 libgvpr2
  libopenexr24 libsdl2-2.0-0 libmysofa1 libmagickcore-6.q16-6 ant-doc
  vlc-plugin-video-splitter libpython2.7-minimal ffmpeg-doc libgvc6
  vlc-plugin-base libpython2.7-stdlib graphviz ant-optional libavresample4
  imagemagick-6-common
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages have been kept back:
  mesa-opencl-icd
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
>>And as you can see there is "1 not upgraded". Apparently this is the problem and I do not know how to fix it.
>>Help!

---

### Post by ubfan1 on 2023-10-04
The usual recomendation for an upgrade is to remove all PPAs you added (deadsnakes,... ) then sudo apt update, sudo apt upgrade, sudo apt full-upgrade, sudo apt dist-upgrade  .That alone might do it, if not then try the release-upgrade

---

### Post by lawrence-joy on 2023-10-18
Hello,
First of all I didn't add any PPAs. They may have been added automatically when downloading software, but I didn't, of myself, add any PPAs.
I tried to get to the list of PPAs using the terminal, but that didn't work. I had to go to the Activities tab in the upper left corner of the main screen and then go the Software & Upgrades, then Other Software. I found a file that had "(deadsnakes...)" in it and was already checked. I picked on it and was able to "remove" it. I then accomplished your terminal commands as given and got the same messages as before "one package not upgraded" and something about upgrade all packages.
I then tried "release-upgrade" and that didn't work.
>>Still need help!

---

### Post by Bashing-om on 2023-10-18
lawrence-joy Well well well ...

Strange still with issues after all this time.

Let's do this afresh.
and all new
show us:
```

sudo apt update
sudo apt upgrade
apt list update-manager-core --installed
grep -i ^prompt /etc/update-manager/release-upgrades

```
and *IF* mesa-opencl-icd is still on hold - show us then:
```

apt policy mesa-opencl-icd

```

[INDENT]we be hunt'n wabbits :D[/INDENT]

---

### Post by lawrence-joy on 2024-06-28
It has been many months since trying to upgrade to 22.04 LTS. I had a medical problem and am now getting back to using Ubuntu.
Following are the commands and output I got when executing the code as given above:

larry@larry-MS-7693:~$ sudo apt update
[sudo] password for larry: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [128 kB]
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
Fetched 128 kB in 1s (106 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
larry@larry-MS-7693:~$ sudo apt list --upgradable
Listing... Done
mesa-opencl-icd/focal-updates,focal-security 21.2.6-0ubuntu0.1~20.04.2 amd64 [upgradable from: 21.0.3-0ubuntu0.3~20.04.4]
N: There are 2 additional versions. Please use the '-a' switch to see them.
larry@larry-MS-7693:~$ sudo apt list --upgradable -a
Listing... Done
mesa-opencl-icd/focal-updates,focal-security 21.2.6-0ubuntu0.1~20.04.2 amd64 [upgradable from: 21.0.3-0ubuntu0.3~20.04.4]
mesa-opencl-icd/now 21.0.3-0ubuntu0.3~20.04.4 amd64 [installed,upgradable to: 21.2.6-0ubuntu0.1~20.04.2]
mesa-opencl-icd/focal 20.0.4-2ubuntu1 amd64

larry@larry-MS-7693:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-bin vlc-plugin-video-output libavformat58 librpmsign8
  libmagick++-6.q16-8 libavfilter7 rpm2cpio ffmpeg vlc-plugin-samba
  graphviz-doc libmagickcore-6.q16-6-extra imagemagick libswresample3
  vlc-plugin-qt libgegl-0.4-0 ant librpmbuild8 libzmq5 libmagickwand-6.q16-6
  vlc-plugin-skins2 libgegl-common vlc-plugin-visualization vlc-l10n
  libcgraph6 debugedit vlc-plugin-notify libvlc5 python3-rpm libpostproc55
  liblab-gamut1 libvlccore9 libvlc-bin librpmio8 imagemagick-6.q16 rpm-common
  rpm-i18n libgsasl7 rpm librpm8 libnetty-java libavcodec58
  libpostgresql-jdbc-java vlc libcdt5 libavutil56 vlc-data libpathplan4
  libavdevice58 libhttpclient-java libswscale5 libgvpr2 libopenexr24
  libsdl2-2.0-0 libmysofa1 libmagickcore-6.q16-6 ant-doc
  vlc-plugin-video-splitter ffmpeg-doc libgvc6 vlc-plugin-base graphviz
  ant-optional libheif1 libavresample4 libde265-0 imagemagick-6-common
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following packages have been kept back:
  mesa-opencl-icd
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
larry@larry-MS-7693:~$ apt list update-manager-core --installed
Listing... Done
update-manager-core/focal-updates,focal-updates,now 1:20.04.10.21 all [installed]
N: There is 1 additional version. Please use the '-a' switch to see it
larry@larry-MS-7693:~$ apt list update-manager-core --installed -a
Listing... Done
update-manager-core/focal-updates,focal-updates,now 1:20.04.10.21 all [installed]
update-manager-core/focal,focal 1:20.04.9 all

larry@larry-MS-7693:~$ grep -i ^prompt /etc/update-manager/release-upgrades
Prompt=lts
larry@larry-MS-7693:~$ 

>>>Hope this is enough information to move forward. Looks like there is still something to delete or upgrade. Next command(s)? Thank you for all the help in the past and going forward.

---

### Post by Bashing-om on 2024-06-28
lawrence-joy -- Yukkie -

Still with "mesa-opencl-icd" not upgrading to the current version - 21.2.6-0ubuntu0.1~20.04.2 :(
As the package is Priority: optional - we can safely remove/purge and then re-install.
```

sudo apt --purge remove mesa-opencl-icd
sudo apt update
sudo apt install mesa-opencl-icd
sudo apt upgrade

```

See here what the package manager says  --- what comes next ?
If this works out we next do-release to upgrade to 22.04.

-leastways - what I think-

---

### Post by lawrence-joy on 2024-07-01
Thank you, thank you, thank you, thank you, thank you. It all seems to be working now. The download ran all Saturday afternoon and Saturday night. There were some question I had to answer, but Sunday morning I got the message that all was up to date.

---

### Post by Bashing-om on 2024-07-01
lawrence-joy; Simply wonderful :D

Glad you got it all dunked out.

[INDENT]happy trails to you
[/INDENT]

---

