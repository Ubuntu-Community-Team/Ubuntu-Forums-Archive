---
title: "the application software updater has closed unexpectedly. Ubuntu 16.04"
date: 2019-05-29
forum: Installation &amp; Upgrades
---

### Post by polaxgr on 2019-05-29
Hi all, i have tried sudo apt-get update , sudo apt-get dist upgrade. But still this application keeps on crashing. I uploaded the crash report, i took 2 screenshots. 

[IMG]https://ibb.co/bszD2Dq[/IMG]https://ibb.co/bszD2Dq
[https://ibb.co/L6YC8RY](https://ibb.co/L6YC8RY)

---

### Post by cruzer001 on 2019-05-29
Hello and welcome to the forums :)

You say apt, but the crash report says update-manager :confused:

Please post the output of
```
sudo apt update
```

---

### Post by polaxgr on 2019-05-30
> **cruzer001 said:**
> Hello and welcome to the forums :)

You say apt, but the crash report says update-manager :confused:

Please post the output of
```
sudo apt update
```

Thanks:)

```
Get:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  InReleaseIgn:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  InRelease
Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release [574 B]
Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release [574 B]
Hit:3 http://gr.archive.ubuntu.com/ubuntu xenial InRelease               
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                     
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:6 http://gr.archive.ubuntu.com/ubuntu xenial-security InRelease [109 kB]   
Ign:7 http://dl.bintray.com/basespace/BaseMount-DEB saucy InRelease            
Hit:8 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu xenial InRelease          
Ign:9 http://dl.bintray.com/basespace/BaseSpaceFS-DEB saucy InRelease          
Get:11 http://dl.google.com/linux/chrome/deb stable Release [943 B]            
Get:12 http://dl.bintray.com/basespace/BaseMount-DEB saucy Release [1838 B]    
Ign:13 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64  InRelease
Hit:14 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease   
Hit:15 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64  Release
Get:16 http://dl.bintray.com/basespace/BaseSpaceFS-DEB saucy Release [1837 B]  
Get:17 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]        
Get:18 http://gr.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]   
Hit:19 http://ppa.launchpad.net/jonathonf/gcc-7.1/ubuntu xenial InRelease      
Get:20 http://gr.archive.ubuntu.com/ubuntu xenial-proposed InRelease [260 kB]  
Hit:21 http://ppa.launchpad.net/marutter/rdev/ubuntu xenial InRelease          
Hit:22 http://gr.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Hit:25 http://ppa.launchpad.net/marutter/rrutter3.5/ubuntu xenial InRelease    
Hit:27 https://cran.rstudio.com/bin/linux/ubuntu xenial/ InRelease             
Hit:28 https://cloud.r-project.org/bin/linux/ubuntu xenial/ InRelease
Hit:29 http://ppa.launchpad.net/noobslab/themes/ubuntu xenial InRelease
Get:30 https://deb.opera.com/opera-stable stable InRelease [2591 B]          
Hit:31 https://download.mono-project.com/repo/ubuntu stable-xenial InRelease   
Get:32 http://gr.archive.ubuntu.com/ubuntu xenial-security/universe Sources [105 kB]
Hit:34 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial InRelease
Get:35 https://packages.microsoft.com/repos/vscode stable InRelease [3182 B]   
Get:36 http://gr.archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [435 kB]
Get:37 http://gr.archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages [378 kB]
Hit:38 http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu xenial InRelease  
Get:39 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1104 B]
Get:40 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [254 kB]
Get:41 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [957 kB]
Get:42 http://gr.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [824 kB]
Get:43 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [748 kB]
Get:44 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [685 kB]
Get:45 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [311 kB]
Hit:46 http://ppa.launchpad.net/ubuntugis/ppa/ubuntu xenial InRelease          
Get:47 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main Sources [17,2 kB]
Get:48 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/universe Sources [4904 B]
Get:49 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages [50,8 kB]
Get:50 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main i386 Packages [37,7 kB]
Get:51 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main Translation-en [22,0 kB]
Get:52 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages [10,7 kB]
Get:53 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/universe i386 Packages [7944 B]
Get:54 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/universe Translation-en [7144 B]
Ign:24 http://www.getdeb.net/ubuntu xenial-getdeb InRelease                    
Hit:55 http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu xenial InRelease
Get:56 https://deb.opera.com/opera-stable stable/non-free amd64 Packages [1807 B]
Hit:57 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Hit:59 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial InRelease
Get:60 https://packages.microsoft.com/repos/vscode stable/main amd64 Packages [119 kB]
Err:58 http://www.getdeb.net/ubuntu xenial-getdeb Release                      
  403  Forbidden
Hit:61 https://ftp.ussg.iu.edu/CRAN/bin/linux/ubuntu xenial/ InRelease         
Reading package lists... Done
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:38
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:38
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:38
E: The repository 'http://archive.getdeb.net/ubuntu xenial-getdeb Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:38
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:38
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list:36 and /etc/apt/sources.list:38



```

---

### Post by cruzer001 on 2019-05-30
Looks like your sources needs some cleanup.  Please post the output of:
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```
Go ahead with the upgrade and also post the results.
```
sudo apt upgrade
```

---

### Post by polaxgr on 2019-05-31
> **cruzer001 said:**
> Looks like your sources needs some cleanup.  Please post the output of:
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```
Go ahead with the upgrade and also post the results.
```
sudo apt upgrade
```

```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#




###### Ubuntu Main Repos
deb http://gr.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse


###### Ubuntu Update Repos
deb http://gr.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner


















deb https://ftp.ussg.iu.edu/CRAN/bin/linux/ubuntu xenial/
deb-src https://ftp.ussg.iu.edu/CRAN/bin/linux/ubuntu xenial/
deb [arch=i386,amd64] https://cran.rstudio.com/bin/linux/ubuntu xenial/
deb-src [arch=i386,amd64] https://cran.rstudio.com/bin/linux/ubuntu xenial/
deb https://cran.rstudio.com/bin/linux/ubuntu xenial/
deb https://cloud.r-project.org/bin/linux/ubuntu/ xenial/
/etc/apt/sources.list.d/basemount.list
/etc/apt/sources.list.d/basespacefs.list
/etc/apt/sources.list.d/cuda-10-0-local-10.0.130-410.48.list
/etc/apt/sources.list.d/cuda.list
/etc/apt/sources.list.d/deadsnakes-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/getdeb.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/jonathonf-ubuntu-gcc-7_1-xenial.list
/etc/apt/sources.list.d/marutter-ubuntu-rdev-xenial.list
/etc/apt/sources.list.d/marutter-ubuntu-rrutter3_5-xenial.list
/etc/apt/sources.list.d/mono-official-stable.list
/etc/apt/sources.list.d/noobslab-ubuntu-themes-xenial.list
/etc/apt/sources.list.d/notepadqq-team-ubuntu-notepadqq-xenial.list
/etc/apt/sources.list.d/opera-stable.list
/etc/apt/sources.list.d/ubuntugis-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/ubuntugis-ubuntu-ubuntugis-unstable-xenial.list
/etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-updates-xenial.list
/etc/apt/sources.list.d/vscode.list
/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list
/etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-xenial.list



```

```
sudo apt upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-144 linux-headers-4.4.0-144-generic linux-image-4.4.0-144-generic linux-modules-4.4.0-144-generic linux-modules-extra-4.4.0-144-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.4.0-150 linux-headers-4.4.0-150-generic linux-image-unsigned-4.4.0-150-generic linux-modules-4.4.0-150-generic linux-modules-extra-4.4.0-150-generic
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra curl fonts-opensymbol intel-microcode libcurl3 libcurl3-gnutls libcurl4-openssl-dev libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-java-common libreoffice-math libreoffice-ogltrans libreoffice-pdfimport libreoffice-report-builder-bin libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  libreoffice-style-breeze libreoffice-style-galaxy libreoffice-writer libsmbclient libwbclient0 linux-generic linux-headers-generic linux-image-generic linux-libc-dev opera-stable
  python-apt python-apt-common python3-apt python3-uno runc samba-libs thunderbird thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us uno-libs3 ure
48 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 265 MB of archives.
After this operation, 302 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://gr.archive.ubuntu.com/ubuntu xenial-security/universe amd64 chromium-codecs-ffmpeg-extra amd64 74.0.3729.169-0ubuntu0.16.04.1 [1106 kB]
Get:2 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-ogltrans amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [73,3 kB]
Get:3 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 ure amd64 5.1.6~rc2-0ubuntu1~xenial7 [1535 kB]
Get:4 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 uno-libs3 amd64 5.1.6~rc2-0ubuntu1~xenial7 [705 kB]
Get:5 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-calc amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [6457 kB]
Get:6 https://deb.opera.com/opera-stable stable/non-free amd64 opera-stable amd64 60.0.3255.109 [66,6 MB]
Get:7 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-impress amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [969 kB]
Get:8 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-draw amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [2403 kB]
Get:9 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-gnome amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [60,7 kB]
Get:10 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-gtk amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [206 kB]
Get:11 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-writer amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [7579 kB]
Get:12 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 libreoffice-report-builder-bin amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [761 kB]
Get:13 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 libreoffice amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [3986 B]
Get:14 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 python3-uno amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [137 kB]
Get:15 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-sdbc-hsqldb amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [107 kB]
Get:16 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-sdbc-firebird amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [3016 B]
Get:17 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-style-galaxy all 1:5.1.6~rc2-0ubuntu1~xenial7 [1523 kB]
Get:18 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-style-breeze all 1:5.1.6~rc2-0ubuntu1~xenial7 [470 kB]
Get:19 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-java-common all 1:5.1.6~rc2-0ubuntu1~xenial7 [1943 kB]
Get:20 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-common all 1:5.1.6~rc2-0ubuntu1~xenial7 [22,4 MB]
Get:21 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-pdfimport amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [182 kB]
Get:22 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-math amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [373 kB]
Get:23 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-base-core amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [716 kB]
Get:24 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-avmedia-backend-gstreamer amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [24,2 kB]                               
Get:25 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-base amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [1519 kB]                                                    
Get:26 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-core amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [28,1 MB]                                                    
Get:27 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 libreoffice-base-drivers amd64 1:5.1.6~rc2-0ubuntu1~xenial7 [509 kB]                                             
Get:28 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 fonts-opensymbol all 2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial7 [104 kB]                                             
Get:29 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 curl amd64 7.47.0-1ubuntu2.13 [139 kB]                                                                           
Get:30 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 libcurl3-gnutls amd64 7.47.0-1ubuntu2.13 [184 kB]                                                                
Get:31 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 samba-libs amd64 2:4.3.11+dfsg-0ubuntu0.16.04.21 [5170 kB]                                                       
Get:32 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 libwbclient0 amd64 2:4.3.11+dfsg-0ubuntu0.16.04.21 [30,3 kB]                                                     
Get:33 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 libsmbclient amd64 2:4.3.11+dfsg-0ubuntu0.16.04.21 [53,2 kB]                                                     
Get:34 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 libcurl4-openssl-dev amd64 7.47.0-1ubuntu2.13 [263 kB]                                                           
Get:35 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 libcurl3 amd64 7.47.0-1ubuntu2.13 [186 kB]                                                                       
Get:36 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 python-apt-common all 1.1.0~beta1ubuntu0.16.04.5 [16,2 kB]                                                       
Get:37 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 python3-apt amd64 1.1.0~beta1ubuntu0.16.04.5 [138 kB]                                                            
Get:38 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-modules-4.4.0-150-generic amd64 4.4.0-150.176 [12,0 MB]                                                    
Get:39 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-image-unsigned-4.4.0-150-generic amd64 4.4.0-150.176 [7050 kB]                                             
Get:40 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-modules-extra-4.4.0-150-generic amd64 4.4.0-150.176 [36,6 MB]                                              
Get:41 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 intel-microcode amd64 3.20190514.0ubuntu0.16.04.2 [2050 kB]                                                      
Get:42 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-generic amd64 4.4.0.150.158 [1788 B]                                                                       
Get:43 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-image-generic amd64 4.4.0.150.158 [2742 B]                                                                 
Get:44 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-4.4.0-150 all 4.4.0-150.176 [10,1 MB]                                                              
Get:45 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-4.4.0-150-generic amd64 4.4.0-150.176 [806 kB]                                                     
Get:46 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-headers-generic amd64 4.4.0.150.158 [2576 B]                                                               
Get:47 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 linux-libc-dev amd64 4.4.0-150.176 [863 kB]                                                                      
Get:48 http://gr.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 python-apt amd64 1.1.0~beta1ubuntu0.16.04.5 [140 kB]                                                             
Get:49 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 thunderbird-locale-en amd64 1:60.7.0+build1-0ubuntu0.16.04.1 [492 kB]                                            
Get:50 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 thunderbird amd64 1:60.7.0+build1-0ubuntu0.16.04.1 [40,3 MB]                                                     
Get:51 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 thunderbird-gnome-support amd64 1:60.7.0+build1-0ubuntu0.16.04.1 [8548 B]                                        
Get:52 http://gr.archive.ubuntu.com/ubuntu xenial-security/main amd64 thunderbird-locale-en-us all 1:60.7.0+build1-0ubuntu0.16.04.1 [10,9 kB]                                          
Get:53 http://gr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 runc amd64 1.0.0~rc7+git20190403.029124da-0ubuntu1~16.04.3 [1889 kB]                                          
Fetched 265 MB in 41s (6448 kB/s)                                                                                                                                                      
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 316218 files and directories currently installed.)
Preparing to unpack .../chromium-codecs-ffmpeg-extra_74.0.3729.169-0ubuntu0.16.04.1_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (74.0.3729.169-0ubuntu0.16.04.1) over (73.0.3683.86-0ubuntu0.16.04.1) ...
Preparing to unpack .../libreoffice-ogltrans_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-ogltrans (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../ure_5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking ure (5.1.6~rc2-0ubuntu1~xenial7) over (5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../uno-libs3_5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking uno-libs3 (5.1.6~rc2-0ubuntu1~xenial7) over (5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-calc_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-calc (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-impress_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-impress (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-draw_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-draw (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-gnome_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-gnome (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-gtk_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-gtk (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-writer_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-writer (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-report-builder-bin_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-report-builder-bin (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../python3-uno_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking python3-uno (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-sdbc-hsqldb_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-sdbc-hsqldb (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-sdbc-firebird_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-sdbc-firebird (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-style-galaxy_1%3a5.1.6~rc2-0ubuntu1~xenial7_all.deb ...
Unpacking libreoffice-style-galaxy (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-style-breeze_1%3a5.1.6~rc2-0ubuntu1~xenial7_all.deb ...
Unpacking libreoffice-style-breeze (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-java-common_1%3a5.1.6~rc2-0ubuntu1~xenial7_all.deb ...
Unpacking libreoffice-java-common (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial7_all.deb ...
Unpacking libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-pdfimport_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-pdfimport (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-math_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-math (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-base-core_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-base-core (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-avmedia-backend-gstreamer (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-base_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-base (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-core_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-core (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../libreoffice-base-drivers_1%3a5.1.6~rc2-0ubuntu1~xenial7_amd64.deb ...
Unpacking libreoffice-base-drivers (1:5.1.6~rc2-0ubuntu1~xenial7) over (1:5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../fonts-opensymbol_2%3a102.7+LibO5.1.6~rc2-0ubuntu1~xenial7_all.deb ...
Unpacking fonts-opensymbol (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial7) over (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial6) ...
Preparing to unpack .../curl_7.47.0-1ubuntu2.13_amd64.deb ...
Unpacking curl (7.47.0-1ubuntu2.13) over (7.47.0-1ubuntu2.12) ...
Preparing to unpack .../libcurl3-gnutls_7.47.0-1ubuntu2.13_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.47.0-1ubuntu2.13) over (7.47.0-1ubuntu2.12) ...
Preparing to unpack .../samba-libs_2%3a4.3.11+dfsg-0ubuntu0.16.04.21_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.21) over (2:4.3.11+dfsg-0ubuntu0.16.04.20) ...
Preparing to unpack .../libwbclient0_2%3a4.3.11+dfsg-0ubuntu0.16.04.21_amd64.deb ...
Unpacking libwbclient0:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.21) over (2:4.3.11+dfsg-0ubuntu0.16.04.20) ...
Preparing to unpack .../libsmbclient_2%3a4.3.11+dfsg-0ubuntu0.16.04.21_amd64.deb ...
Unpacking libsmbclient:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.21) over (2:4.3.11+dfsg-0ubuntu0.16.04.20) ...
Preparing to unpack .../libcurl4-openssl-dev_7.47.0-1ubuntu2.13_amd64.deb ...
Unpacking libcurl4-openssl-dev:amd64 (7.47.0-1ubuntu2.13) over (7.47.0-1ubuntu2.12) ...
Preparing to unpack .../libcurl3_7.47.0-1ubuntu2.13_amd64.deb ...
Unpacking libcurl3:amd64 (7.47.0-1ubuntu2.13) over (7.47.0-1ubuntu2.12) ...
Preparing to unpack .../opera-stable_60.0.3255.109_amd64.deb ...
Unpacking opera-stable (60.0.3255.109) over (60.0.3255.95) ...
Preparing to unpack .../python-apt-common_1.1.0~beta1ubuntu0.16.04.5_all.deb ...
Unpacking python-apt-common (1.1.0~beta1ubuntu0.16.04.5) over (1.1.0~beta1ubuntu0.16.04.4) ...
Preparing to unpack .../python3-apt_1.1.0~beta1ubuntu0.16.04.5_amd64.deb ...
Unpacking python3-apt (1.1.0~beta1ubuntu0.16.04.5) over (1.1.0~beta1ubuntu0.16.04.4) ...
Selecting previously unselected package linux-modules-4.4.0-150-generic.
Preparing to unpack .../linux-modules-4.4.0-150-generic_4.4.0-150.176_amd64.deb ...
Unpacking linux-modules-4.4.0-150-generic (4.4.0-150.176) ...
Selecting previously unselected package linux-image-unsigned-4.4.0-150-generic.
Preparing to unpack .../linux-image-unsigned-4.4.0-150-generic_4.4.0-150.176_amd64.deb ...
Unpacking linux-image-unsigned-4.4.0-150-generic (4.4.0-150.176) ...
Selecting previously unselected package linux-modules-extra-4.4.0-150-generic.
Preparing to unpack .../linux-modules-extra-4.4.0-150-generic_4.4.0-150.176_amd64.deb ...
Unpacking linux-modules-extra-4.4.0-150-generic (4.4.0-150.176) ...
Preparing to unpack .../intel-microcode_3.20190514.0ubuntu0.16.04.2_amd64.deb ...
Unpacking intel-microcode (3.20190514.0ubuntu0.16.04.2) over (3.20190514.0ubuntu0.16.04.1) ...
Preparing to unpack .../linux-generic_4.4.0.150.158_amd64.deb ...
Unpacking linux-generic (4.4.0.150.158) over (4.4.0.149.157) ...
Preparing to unpack .../linux-image-generic_4.4.0.150.158_amd64.deb ...
Unpacking linux-image-generic (4.4.0.150.158) over (4.4.0.149.157) ...
Selecting previously unselected package linux-headers-4.4.0-150.
Preparing to unpack .../linux-headers-4.4.0-150_4.4.0-150.176_all.deb ...
Unpacking linux-headers-4.4.0-150 (4.4.0-150.176) ...
Selecting previously unselected package linux-headers-4.4.0-150-generic.
Preparing to unpack .../linux-headers-4.4.0-150-generic_4.4.0-150.176_amd64.deb ...
Unpacking linux-headers-4.4.0-150-generic (4.4.0-150.176) ...
Preparing to unpack .../linux-headers-generic_4.4.0.150.158_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.150.158) over (4.4.0.149.157) ...
Preparing to unpack .../linux-libc-dev_4.4.0-150.176_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-150.176) over (4.4.0-149.175) ...
Preparing to unpack .../python-apt_1.1.0~beta1ubuntu0.16.04.5_amd64.deb ...
Unpacking python-apt (1.1.0~beta1ubuntu0.16.04.5) over (1.1.0~beta1ubuntu0.16.04.4) ...
Preparing to unpack .../thunderbird-locale-en_1%3a60.7.0+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:60.7.0+build1-0ubuntu0.16.04.1) over (1:60.6.1+build2-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird_1%3a60.7.0+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird (1:60.7.0+build1-0ubuntu0.16.04.1) over (1:60.6.1+build2-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a60.7.0+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:60.7.0+build1-0ubuntu0.16.04.1) over (1:60.6.1+build2-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a60.7.0+build1-0ubuntu0.16.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:60.7.0+build1-0ubuntu0.16.04.1) over (1:60.6.1+build2-0ubuntu0.16.04.1) ...
Preparing to unpack .../runc_1.0.0~rc7+git20190403.029124da-0ubuntu1~16.04.3_amd64.deb ...
Unpacking runc (1.0.0~rc7+git20190403.029124da-0ubuntu1~16.04.3) over (1.0.0~rc7+git20190403.029124da-0ubuntu1~16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1.1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Setting up chromium-codecs-ffmpeg-extra (74.0.3729.169-0ubuntu0.16.04.1) ...
Setting up uno-libs3 (5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up ure (5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up fonts-opensymbol (2:102.7+LibO5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libcurl3-gnutls:amd64 (7.47.0-1ubuntu2.13) ...
Setting up curl (7.47.0-1ubuntu2.13) ...
Setting up libwbclient0:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.21) ...
Setting up samba-libs:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.21) ...
Setting up libsmbclient:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.21) ...
Setting up libcurl3:amd64 (7.47.0-1ubuntu2.13) ...
Setting up libcurl4-openssl-dev:amd64 (7.47.0-1ubuntu2.13) ...
Setting up opera-stable (60.0.3255.109) ...
Setting up python-apt-common (1.1.0~beta1ubuntu0.16.04.5) ...
Setting up python3-apt (1.1.0~beta1ubuntu0.16.04.5) ...
Setting up linux-modules-4.4.0-150-generic (4.4.0-150.176) ...
Setting up linux-image-unsigned-4.4.0-150-generic (4.4.0-150.176) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.4.0-149-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.4.0-149-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-4.4.0-150-generic
I: /initrd.img is now a symlink to boot/initrd.img-4.4.0-150-generic
Setting up linux-modules-extra-4.4.0-150-generic (4.4.0-150.176) ...
Setting up intel-microcode (3.20190514.0ubuntu0.16.04.2) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting up linux-image-generic (4.4.0.150.158) ...
Setting up linux-headers-4.4.0-150 (4.4.0-150.176) ...
Setting up linux-headers-4.4.0-150-generic (4.4.0-150.176) ...
Setting up linux-headers-generic (4.4.0.150.158) ...
Setting up linux-generic (4.4.0.150.158) ...
Setting up linux-libc-dev:amd64 (4.4.0-150.176) ...
Setting up python-apt (1.1.0~beta1ubuntu0.16.04.5) ...
Setting up thunderbird (1:60.7.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en (1:60.7.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-gnome-support (1:60.7.0+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en-us (1:60.7.0+build1-0ubuntu0.16.04.1) ...
Setting up runc (1.0.0~rc7+git20190403.029124da-0ubuntu1~16.04.3) ...
Setting up libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up libreoffice-style-galaxy (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-style-breeze (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-core (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-draw (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-impress (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-ogltrans (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-base-core (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-calc (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-gtk (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-gnome (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-writer (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-base-drivers (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-base (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-report-builder-bin (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-math (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-java-common (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up python3-uno (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-sdbc-hsqldb (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-sdbc-firebird (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Setting up libreoffice-pdfimport (1:5.1.6~rc2-0ubuntu1~xenial7) ...
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Processing triggers for linux-image-unsigned-4.4.0-150-generic (4.4.0-150.176) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.4.0-150-generic
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-150-generic
Found initrd image: /boot/initrd.img-4.4.0-150-generic
Found linux image: /boot/vmlinuz-4.4.0-149-generic
Found initrd image: /boot/initrd.img-4.4.0-149-generic
Found linux image: /boot/vmlinuz-4.4.0-147-generic
Found initrd image: /boot/initrd.img-4.4.0-147-generic
Found linux image: /boot/vmlinuz-4.4.0-144-generic
Found initrd image: /boot/initrd.img-4.4.0-144-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Processing triggers for initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-150-generic



```

---

### Post by cruzer001 on 2019-05-31
Ok, not bad at all.  Did see one error (getdeb) and one warning (grub_timeout), but not a big thing.

You have for some reason manually modified your sources, but again no big deal.  Its all working.

Lets finish this upgrade and then get back to the update manager.
```
sudo apt full-upgrade
```
then **reboot** and..
```
sudo apt autoremove
```
followed with
```
sudo apt autoclean
```

Now try the update manager again, just to see if it will crash.

---

### Post by #&amp;thj^% on 2019-05-31
Along with the advice already given, is there a real need to have:
```
deb http://gr.archive.ubuntu.com/ubuntu/ **xenial-proposed main **restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/** xenial-proposed main** restricted universe multiverse
```
enabled?

---

### Post by cruzer001 on 2019-05-31
Thankyou 1fallen, I was going to ask about that.

Edit
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by polaxgr on 2019-06-03
> **cruzer001 said:**
> Ok, not bad at all.  Did see one error (getdeb) and one warning (grub_timeout), but not a big thing.

You have for some reason manually modified your sources, but again no big deal.  Its all working.

Lets finish this upgrade and then get back to the update manager.
```
sudo apt full-upgrade
```
then **reboot** and..
```
sudo apt autoremove
```
followed with
```
sudo apt autoclean
```

Now try the update manager again, just to see if it will crash.

thanks a lot for the help! Though it seems that it still crashes

---

### Post by cruzer001 on 2019-06-03
It "seems" to crash?

Or are you getting a crash report?

```
sudo rm /var/crash/*
```

That will clear (reset) all crash reports.

If you still having a crash, open it in terminal and see what that tells you.
```
update-manager
```

And do a version check since you have "proposed" open.
```
apt-cache policy update-manager
```

---

### Post by polaxgr on 2019-06-04
> **cruzer001 said:**
> It "seems" to crash?

Or are you getting a crash report?

```
sudo rm /var/crash/*
```

That will clear (reset) all crash reports.

If you still having a crash, open it in terminal and see what that tells you.
```
update-manager
```

And do a version check since you have "proposed" open.
```
apt-cache policy update-manager
```

it is crashing yes. 
[https://ibb.co/1TfC57G](https://ibb.co/1TfC57G)
[https://ibb.co/7Wd5F6f](https://ibb.co/7Wd5F6f)
i uploaded the crash report

---

### Post by cruzer001 on 2019-06-04
In the title of your crash report.
> "update-manager crashed with..........dbus error spawn........."
I get a lot of hits on this including similar launchpad bugs, but haven't hit on a good fix.

I would suggest using Synaptic Package Manager for updating for now, until this can be resolved.
```
sudo apt install synaptic
```
[https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel](https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel)

[https://www.lifewire.com/guide-to-synaptic-package-manager-2205707](https://www.lifewire.com/guide-to-synaptic-package-manager-2205707)

---

### Post by polaxgr on 2019-06-10
> **cruzer001 said:**
> In the title of your crash report.

I get a lot of hits on this including similar launchpad bugs, but haven't hit on a good fix.

I would suggest using Synaptic Package Manager for updating for now, until this can be resolved.
```
sudo apt install synaptic
```
[https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel](https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel)

[https://www.lifewire.com/guide-to-synaptic-package-manager-2205707](https://www.lifewire.com/guide-to-synaptic-package-manager-2205707)

synaptic also crashes.

---

### Post by cruzer001 on 2019-06-10
So you have two package managers that are crashing.  Any other applications crashing?  Synaptic and Update-manager operate together, but are independent of each other.  Try opening synaptic and in terminal and look for errors in the terminal.
```
pkexec synaptic
```

If there has been any crash reports generated, please post those.

And just to cover your graphic model and driver; ram usage.  Post:
```
lshw -c video && free -m
```

Is this a recent version upgrade, maybe from 14.04?  Maybe upgraded by editing your sources list?

And look here for errors (in red).
```
journalctl -b
```

There is also the matter of "proposed" being open to include "backports".  Proposed has been asked about eariler.

Currently I am not sure what direction to look in, maybe this will get us on course.

---

### Post by polaxgr on 2019-06-12
> **cruzer001 said:**
> So you have two package managers that are crashing.  Any other applications crashing?  Synaptic and Update-manager operate together, but are independent of each other.  Try opening synaptic and in terminal and look for errors in the terminal.
```
pkexec synaptic
```

If there has been any crash reports generated, please post those.

And just to cover your graphic model and driver; ram usage.  Post:
```
lshw -c video && free -m
```

Is this a recent version upgrade, maybe from 14.04?  Maybe upgraded by editing your sources list?

And look here for errors (in red).
```
journalctl -b
```

There is also the matter of "proposed" being open to include "backports".  Proposed has been asked about eariler.

Currently I am not sure what direction to look in, maybe this will get us on course.

via terminal i can open it but it doesnt upgrade packages. No errors (in red).

so this way i can upgrade ? sofware updater still crashes

---

