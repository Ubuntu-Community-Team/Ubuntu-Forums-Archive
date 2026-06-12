---
title: "Updates won't install"
date: 2018-12-04
forum: Installation &amp; Upgrades
---

### Post by terence4 on 2018-12-04
Hello folks,

I can't update to the latest Ubuntu.
I think my problems started when I tried from the software centre.
 
It wouldn't successfully update and now I can't load any new programs.
If I try to update it starts, then stops.

Is there a simple way of finding the problem?

---

### Post by Impavidus on 2018-12-04
Maybe your package manager somehow got messed up.

Try these two commands one at a time:```
sudo apt update
sudo apt upgrade
```and post the output. That should tell us a bit more.

---

### Post by terence4 on 2018-12-04
Hi, thanks for the reply.

sudo apt upgrade

```
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [451 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [397 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [168 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [234 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [99.0 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [585 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [580 kB]
Ign:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages   
Ign:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages    
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [160 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [195 kB]
Ign:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en   
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Hit:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons
Ign:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [319 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 Packages [3,468 B]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 Packages [3,476 B]
Ign:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe Translation-en
Ign:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages
Ign:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata
Hit:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe DEP-11 64x64 Icons
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe Translation-en [1,604 B]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,816 B]
Ign:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [10.6 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [20.1 kB]
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 Packages
Err:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en
  Hash Sum mismatch
Err:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata
  
Err:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons
  Hash Sum mismatch
Err:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe DEP-11 64x64 Icons
  Hash Sum mismatch
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 Packages
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse Translation-en
Ign:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
Ign:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages
Ign:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en
Ign:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
Ign:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages
Ign:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en
Fetched 2,622 kB in 1s (1,431 kB/s)

** (appstreamcli:4682): WARNING **: No origin found for file security.ubuntu.com_ubuntu_dists_bionic-security_restricted_dep11_Components-amd64.yml.gz

** (appstreamcli:4682): WARNING **: No origin found for file security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_dep11_Components-amd64.yml.gz

** (appstreamcli:4682): WARNING **: No origin found for file security.ubuntu.com_ubuntu_dists_bionic-security_main_dep11_Components-amd64.yml.gz

** (appstreamcli:4682): WARNING **: No origin found for file gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_dep11_Components-amd64.yml.gz
Segmentation fault (core dumped)
Reading package lists... Error!
E: Failed to fetch store:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_i18n_Translation-en.xz  Hash Sum mismatch
E: Failed to fetch store:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_dep11_Components-amd64.yml.xz  
E: Failed to fetch store:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_dep11_icons-64x64.tar.gz  Hash Sum mismatch
E: Failed to fetch store:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_bionic-security_main_dep11_icons-64x64.tar.gz  Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_i18n_Translation-en (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
```

terence@terence-LIFEBOOK-A514:~$ sudo apt update
```
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
Ign:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en    
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [451 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [397 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [168 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [234 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [99.0 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [585 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Hit:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons
Ign:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [580 kB]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [160 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [195 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [319 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 Packages [3,468 B]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 Packages [3,476 B]
Ign:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe Translation-en
Ign:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata
Hit:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe DEP-11 64x64 Icons
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe Translation-en [1,604 B]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,816 B]
Ign:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages
Ign:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [10.6 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [20.1 kB]
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 Packages
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 Packages
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse Translation-en
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
Err:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons
  Hash Sum mismatch
Ign:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en
Ign:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
Ign:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages
Err:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en
  Hash Sum mismatch
Ign:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en
Err:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata
  
Err:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe DEP-11 64x64 Icons
  Hash Sum mismatch
Ign:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 Packages
Ign:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 Packages
Ign:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse Translation-en
Fetched 609 kB in 1s (346 kB/s)

** (appstreamcli:4910): WARNING **: No origin found for file security.ubuntu.com_ubuntu_dists_bionic-security_restricted_dep11_Components-amd64.yml.gz

** (appstreamcli:4910): WARNING **: No origin found for file security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_dep11_Components-amd64.yml.gz

** (appstreamcli:4910): WARNING **: No origin found for file security.ubuntu.com_ubuntu_dists_bionic-security_main_dep11_Components-amd64.yml.gz

** (appstreamcli:4910): WARNING **: No origin found for file gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_dep11_Components-amd64.yml.gz
Segmentation fault (core dumped)
Reading package lists... Error!
E: Failed to fetch store:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_bionic-security_main_dep11_icons-64x64.tar.gz  Hash Sum mismatch
E: Failed to fetch store:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_i18n_Translation-en.xz  Hash Sum mismatch
E: Failed to fetch store:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_dep11_Components-amd64.yml.xz  
E: Failed to fetch store:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_dep11_icons-64x64.tar.gz  Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_restricted_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_multiverse_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_binary-amd64_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_i18n_Translation-en%5fGB (1)
E: Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_i18n_Translation-en (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
```

Should I try sudo apt-get update?

---

### Post by terence4 on 2018-12-04
Did I get hacked?

The second half of one of my text files went half Chinese, as follows;

ENJMEW 
 
 
&#2573;&#26624;&#29696;&#29696;&#28672;&#29440;&#14848;&#12032;&#12032;&#30464;&#30464;&#30464;&#11776;&#26112;&#24832;&#25344;&#25856;&#25088;&#28416;&#28416;&#27392;&#11776;&#25344;&#28416;&#27904;&#12032;&#28672;&#24832;&#26368;&#25856;&#29440;&#12032;&#20224;&#27648;&#26880;&#30208;&#25856;&#11520;&#19456;&#25856;&#24832;&#26112;&#11520;&#17664;&#30720;&#29696;&#29184;&#24832;&#25344;&#29696;&#12032;&#13056;&#13824;&#14336;&#12800;&#12544;&#13312;&#13056;&#13824;&#14592;&#14592;&#13568;&#13568;&#12800;&#12288;&#12544;&#3328;&#2560;&#3328;&#2560;&#16640;&#25088;&#28416;&#29952;&#29696;&#11520;&#20224;&#27648;&#26880;&#30208;&#25856;&#11520;&#19456;&#25856;&#24832;&#26112;&#11520;&#17664;&#30720;&#29696;&#29184;&#24832;&#25344;&#29696;&#11776;&#25344;&#28416;&#27904;&#3328;&#2560;&#16640;&#28672;&#28672;&#8192;&#18688;&#17408;&#14848;&#8192;&#12544;&#13824;&#13312;&#12544;&#13568;&#13056;&#14336;&#14592;&#13056;&#14080;&#13312;&#14592;&#14080;&#12288;&#14592;&#3328;&#2560;&#16640;&#28672;&#28672;&#8192;&#21248;&#25856;&#25344;&#29184;&#25856;&#29696;&#14848;&#8192;&#25088;&#12544;&#25856;&#14592;&#25344;&#25600;&#14592;&#14592;&#14592;&#12544;&#12288;&#13312;&#14080;&#12800;&#13568;&#12544;&#25344;&#13824;&#13568;&#25600;&#13568;&#25344;&#25856;&#14336;&#24832;&#26112;&#14592;&#13568;&#12800;&#14336;&#26112;&#14336;&#10240;&#29184;&#25856;&#29440;&#25856;&#29696;&#10496;&#8192;&#3328;&#2560;&#3328;&#2560;&#16640;&#27904;&#24832;&#31232;&#28416;&#28160;&#8192;&#16640;&#29440;&#29440;&#28416;&#25344;&#26880;&#24832;&#29696;&#25856;&#29440;&#3328;&#2560;&#3328;&#2560;&#17152;&#24832;&#28160;&#24832;&#25600;&#24832;&#3328;&#2560;&#24832;&#25088;&#28416;&#29952;&#29696;&#28416;&#27648;&#26880;&#30208;&#25856;&#27648;&#12288;&#13824;&#11520;&#12800;&#12288;&#3328;&#2560;&#26624;&#28416;&#28672;&#11776;&#11776;&#11776;&#3328;&#2560;&#3328;&#2560;&#29440;&#24832;&#27904;&#25856;&#8192;&#24832;&#29440;&#8192;&#24832;&#25088;&#28416;&#30208;&#25856;&#3328;&#2560;&#3328;&#2560;&#16640;&#27904;&#24832;&#31232;&#28416;&#28160;&#8192;&#27904;&#25856;&#29184;&#25344;&#26624;&#24832;&#28160;&#29696;&#8192;&#24832;&#25344;&#25344;&#8192;&#29952;&#27392;&#3328;&#2560;&#24832;


plus a whole lot more.

---

### Post by ajgreeny on 2018-12-04
Try running ```
sudo rm -R /var/lib/apt/lists/*
``` then run ```
sudo apt update && sudo apt upgrade
``` which should remove the corrupt list files and then rebuild them and hopefully upgrade without a problem.

---

### Post by terence4 on 2018-12-05
This is what I get.

```
terence@terence-LIFEBOOK-A514:~$ sudo rm -R /var/lib/apt/lists/*
rm: cannot remove '/var/lib/apt/lists/*': No such file or directory
terence@terence-LIFEBOOK-A514:~$ sudo apt update && sudo apt upgrade
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [218 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [168 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1,019 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [84.0 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons [29 B]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [101 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [99.8 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [56.5 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [10.6 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [20.1 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 Packages [1,440 B]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 Packages [1,608 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse Translation-en [996 B]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main i386 Packages [1,007 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en_GB [432 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en [516 kB]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 DEP-11 Metadata [477 kB]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main DEP-11 64x64 Icons [245 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted amd64 Packages [9,184 B]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted i386 Packages [9,156 B]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted Translation-en_GB [2,072 B]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted Translation-en [3,584 B]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages [8,570 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe i386 Packages [8,531 kB]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe Translation-en_GB [4,118 kB]
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe Translation-en [4,941 kB]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 DEP-11 Metadata [3,287 kB]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe DEP-11 64x64 Icons [8,420 kB]
Get:34 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 Packages [151 kB]
Get:35 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse i386 Packages [144 kB]
Get:36 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse Translation-en_GB [82.1 kB]
Get:37 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse Translation-en [108 kB]
Get:38 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]
Get:39 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse DEP-11 64x64 Icons [225 kB]
Get:40 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [454 kB]
Get:41 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [397 kB]
Get:42 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [169 kB]
Get:43 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [234 kB]
Get:44 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [99.0 kB]
Get:45 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [6,992 B]
Get:46 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 Packages [6,928 B]
Get:47 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [3,076 B]
Get:48 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [588 kB]
Get:49 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [581 kB]
Get:50 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [161 kB]
Get:51 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [195 kB]
Get:52 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [326 kB]
Get:53 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [6,364 B]
Get:54 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [6,520 B]
Get:55 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse Translation-en [3,356 B]
Get:56 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:57 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse DEP-11 64x64 Icons [2,638 B]
Get:58 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 Packages [3,468 B]
Get:59 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 Packages [3,476 B]
Get:60 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe Translation-en [1,604 B]
Get:61 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,816 B]
Get:62 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe DEP-11 64x64 Icons [29 B]
Fetched 46.9 MB in 14s (3,343 kB/s)                                            

(appstreamcli:3373): GLib-CRITICAL **: g_strchug: assertion 'string != NULL' failed

(appstreamcli:3373): GLib-CRITICAL **: g_strchomp: assertion 'string != NULL' failed

(appstreamcli:3373): GLib-CRITICAL **: g_strchug: assertion 'string != NULL' failed

(appstreamcli:3373): GLib-CRITICAL **: g_strchomp: assertion 'string != NULL' failed
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1855 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f installsudo&#8217; to correct these.
The following packages have unmet dependencies.
 libperl5.22 : Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.3) but 5.22.1-9ubuntu0.2 is installed
 perl : Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.3) but 5.22.1-9ubuntu0.2 is installed
E: Unmet dependencies. Try using -f.

I tried sudo apt-get -f install and got the following;

terence@terence-LIFEBOOK-A514:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 libperl5.22 : Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.3) but 5.22.1-9ubuntu0.2 is installed
 perl : Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.3) but 5.22.1-9ubuntu0.2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies 
```

---

### Post by Impavidus on 2018-12-05
You've got an awful lot of packages to be upgraded (more than half of them?) and you've got perl 5.22, which belongs to Ubuntu 16.04, but you're running Ubuntu 18.04, which comes with perl 5.26. And it's even an old version for Ubuntu 16.04, as you should have version 5.22.1-9ubuntu0.6, not 5.22.1-9ubuntu0.2 or 5.22.1-9ubuntu0.3.

Let's find out why this is happening.```
apt-cache policy libperl5.26 libperl5.22 perl-modules-5.26 perl-modules-5.22 perl
```
You wrote that you can't update to the latest release of Ubuntu. It appears that you're already on the latest LTS release of Ubuntu, which should be good enough for many users, but maybe something went wrong during a previous upgrade from 16.04 to 18.04. Is there anything about the history of your system that we should know? And, although release upgrades tend to work well (in my experience at least; not everybody agrees), fixing a release upgrade gone wrong can be very hard, to the extend that a fresh install is usually better. We can try to fix this, but it's your choice.

---

### Post by terence4 on 2018-12-05
Thanks again for the response.
Below is what I get with the above command.

I remember with my first installation I lost windows 10 altogether, it wasn't an option any more although I intended to have both systems. I repaired windows and uploaded Ubuntu again and got the same result. I decided to only use Ubuntu.
When I upgraded to 16.04 LTS I think it was a new install again if I remember correctly.
I tried the latest update recently and it almost worked but eventually failed.
If possible I would like a fix but if I have to will do a fresh install.
Time is not on my side at the moment so the quickest option will be the best one.


```
terence@terence-LIFEBOOK-A514:~$ apt-cache policy libperl5.26 perl-modules-5.22 perl 
libperl5.26:
  Installed: (none)
  Candidate: 5.26.1-6ubuntu0.3
  Version table:
     5.26.1-6ubuntu0.3 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     5.26.1-6 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
perl-modules-5.22:
  Installed: 5.22.1-9ubuntu0.2
  Candidate: 5.22.1-9ubuntu0.2
  Version table:
 *** 5.22.1-9ubuntu0.2 100
        100 /var/lib/dpkg/status
perl:
  Installed: 5.22.1-9ubuntu0.3
  Candidate: 5.26.1-6ubuntu0.3
  Version table:
     5.26.1-6ubuntu0.3 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     5.26.1-6 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
 *** 5.22.1-9ubuntu0.3 100
        100 /var/lib/dpkg/status
```

---

### Post by terence4 on 2018-12-05
P.S. I'm in a different time zone so if I don't continue now I'm not being ungrateful or presumptious - just need to go to bed.

---

### Post by Impavidus on 2018-12-06
Your software sources were updated to 18.04, but it seems your software (at least perl, but probably more) is still from 16.04 and not even fully updated for that release. I think your 16.04 system was already broken, which caused the upgrade to 18.04 to fail. A fresh install is the fastest solution. After downloading the live disk, it shouldn't take more than an hour.

This problem is hard to fix. There's a version conflict within perl 5.22, but that's no longer available from your repositories so you can't fix it by upgrading all perl-related packages to the latest version.

---

### Post by terence4 on 2018-12-06
OK that's the way I'll go then.

Downloading the live disk?

Is there a post I can read how to do it right?

---

