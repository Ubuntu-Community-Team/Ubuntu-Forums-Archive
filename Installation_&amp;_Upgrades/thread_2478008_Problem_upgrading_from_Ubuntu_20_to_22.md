---
title: "Problem upgrading from Ubuntu 20 to 22"
date: 2022-08-14
forum: Installation &amp; Upgrades
---

### Post by jcpfuntner on 2022-08-14
I'm trying to follow steps at [https://linuxconfig.org/how-to-upgrade-ubuntu-to-22-04-lts-jammy-jellyfish](https://linuxconfig.org/how-to-upgrade-ubuntu-to-22-04-lts-jammy-jellyfish) to upgrade and the upgrade utility says I haven't installed available updates:

```

# do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] yes
W: APT had planned for dpkg to do more than it reported back (0 vs 3).
   Affected packages: grub-pc:amd64
# do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
# 

```

Does anyone have any advice?

---

### Post by tea for one on 2022-08-14
> **jcpfuntner said:**
> I'm trying to follow steps at [https://linuxconfig.org/how-to-upgrade-ubuntu-to-22-04-lts-jammy-jellyfish](https://linuxconfig.org/how-to-upgrade-ubuntu-to-22-04-lts-jammy-jellyfish) to upgrade and the upgrade utility says I haven't installed available updates:

```

# do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] yes
W: APT had planned for dpkg to do more than it reported back (0 vs 3).
   Affected packages: grub-pc:amd64
# do-release-upgrade
Checking for a new Ubuntu release
[COLOR="#0000FF"]Please install all available updates for your release before upgrading[/COLOR]. 
# 

```

Does anyone have any advice?

The highlighted text in blue is relevant.
What happened when you performed step 1 from the guide you are using?

---

### Post by jcpfuntner on 2022-08-14
I reran the first three steps and ran a command that [FONT=courier new]apt update[/FONT] suggested

```

# apt update
Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal InRelease                                                            
Hit:3 [https://ocean.surfshark.com/debian](https://ocean.surfshark.com/debian) stretch InRelease                                                                  
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                                                                                                   
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]                                                                                  
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]                                                                                  
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]                                                                                          
Hit:9 [http://ppa.launchpad.net/system76-dev/stable/ubuntu](http://ppa.launchpad.net/system76-dev/stable/ubuntu) focal InRelease                                      
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [278 kB]
Hit:8 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease 
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [391 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/main amd64 DEP-11 Metadata [7,992 B]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [30.5 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [40.8 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [77.6 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Hit:18 [http://apt.postgresql.org/pub/repos/apt](http://apt.postgresql.org/pub/repos/apt) focal-pgdg InRelease          
Err:19 [https://ookla.bintray.com/debian](https://ookla.bintray.com/debian) generic InRelease
  502  Bad Gateway [IP: 35.166.126.94 443]
Fetched 1,165 kB in 6s (208 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://apt.postgresql.org/pub/repos/apt focal-pgdg InRelease' doesn't support architecture 'i386'
W: Failed to fetch [https://ookla.bintray.com/debian/dists/generic/InRelease](https://ookla.bintray.com/debian/dists/generic/InRelease)  502  Bad Gateway [IP: 35.166.126.94 443]
W: Some index files failed to download. They have been ignored, or old ones used instead.
# apt list --upgradable
Listing... Done
grub-common/focal-updates 2.04-1ubuntu26.15 amd64 [upgradable from: 2.04-1ubuntu26.4]
grub-pc-bin/focal-updates 2.04-1ubuntu26.15 amd64 [upgradable from: 2.04-1ubuntu26.4]
grub-pc/focal-updates 2.04-1ubuntu26.15 amd64 [upgradable from: 2.04-1ubuntu26.4]
grub2-common/focal-updates 2.04-1ubuntu26.15 amd64 [upgradable from: 2.04-1ubuntu26.4]
# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] yes
W: APT had planned for dpkg to do more than it reported back (0 vs 3).
   Affected packages: grub-pc:amd64
# apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] yes
W: APT had planned for dpkg to do more than it reported back (0 vs 3).
   Affected packages: grub-pc:amd64
# 

```

---

### Post by tea for one on 2022-08-14
You have some unusual repo sources for an in situ upgrade.
If you remove the non-ubuntu sources e.g. the the debian repositories, you may be able to complete the upgrade.

---

