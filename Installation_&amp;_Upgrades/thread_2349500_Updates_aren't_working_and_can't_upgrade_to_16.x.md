---
title: "Updates aren't working and can't upgrade to 16.x"
date: 2017-01-15
forum: Installation &amp; Upgrades
---

### Post by chaz72 on 2017-01-15
Hey all. I'm fairly new to Ubuntu. I've used from time to time over the years and about a year ago I decided I needed to learn due to the nature of my job, so I run Ubuntu natively now on my laptop. Everything has been working great, GNS3, VMWare workstation, etc, but now all the sudden I can't do updates, nor upgrade to the latest release of Ubuntu. I'm currently running 14.04 I believe. Can anyone help me out here? When I run sudo apt-get update I get the below. I've tried sudo apt-get clean, apt-get autoclean, apt-get upgrade, and none are working.

When running apt-get update:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease)  Unable to find expected entry 'restricted/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  Unable to find expected entry 'universe/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/gns3/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/gns3/ppa/ubuntu/dists/trusty/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/numix/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/numix/ppa/ubuntu/dists/trusty/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release](http://extras.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/Release](http://archive.canonical.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'partner/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Error after trying to upgrade to 16.x:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease)  Unable to find expected entry 'restricted/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Unable to find expected entry 'universe/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Note: I've made no changes to my laptop.

Thanks!

Chaz.

---

### Post by jeremy31 on 2017-01-15
Can you ping anything?  ```
ping -c3 8.8.8.8
```
```
ping -c3 google.com
```

You could post results for ```
cat /etc/apt/sources.list
```

The duplicate posts happen from time to time, it seems to be a vBulletin 4 issue

---

### Post by chaz72 on 2017-01-16
Yes, I have full network reachability. That's what is odd... The results for the sources list is below.

```
cscecela@Kalibu:~$ ping -c3 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=58 time=15.3 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=58 time=22.4 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=58 time=14.7 ms

--- 4.2.2.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 14.729/17.521/22.454/3.499 ms

cscecela@Kalibu:~$ ping -c3 google.com
PING google.com (172.217.7.174) 56(84) bytes of data.
64 bytes from iad30s09-in-f14.1e100.net (172.217.7.174): icmp_seq=1 ttl=53 time=26.3 ms
64 bytes from iad30s09-in-f14.1e100.net (172.217.7.174): icmp_seq=2 ttl=53 time=25.7 ms
64 bytes from iad30s09-in-f14.1e100.net (172.217.7.174): icmp_seq=3 ttl=53 time=24.4 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 24.479/25.537/26.367/0.787 ms

cscecela@Kalibu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe multiverse restricted main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe multiverse restricted main #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed restricted main universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed restricted main universe multiverse #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports universe multiverse restricted main
```

---

### Post by chaz72 on 2017-01-16
Sorry. Thank you for responding!

Chaz.

---

### Post by chaz72 on 2017-01-17
Bump. Anyone? Thanks!

---

### Post by chaz72 on 2017-01-17
Ahh. Woke up this morning to the red circle above with the error message in the screen shot. Any help would be greatly appreciated. I'm not sure why this is occurring. No changes have been made to my system and I really don't want to do a re-install. 

Thank you,

Chaz.[img]https://pomeroy-my.sharepoint.com/personal/ccecela_cntr_pomeroy_com/_layouts/15/guestaccess.aspx?guestaccesstoken=6PiYby4vAljEM3jiLw4dt1gayhRQGWd8t3TQI%2fimi40%3d&docid=1fe7fd8bef8dd43c494b37c1c24e99d0f&rev=1[/img]

---

### Post by jeremy31 on 2017-01-17
What does ```
cat /etc/lsb-release
```

---

### Post by Impavidus on 2017-01-18
Why is there a 9? It should be binary-[COLOR=#ff0000]**i**[/COLOR]386. Or binary-amd64.

> **chaz72 said:**
> Hey all. I'm fairly new to Ubuntu. I've used from time to time over the years and about a year ago I decided I needed to learn due to the nature of my job, so I run Ubuntu natively now on my laptop. Everything has been working great, GNS3, VMWare workstation, etc, but now all the sudden I can't do updates, nor upgrade to the latest release of Ubuntu. I'm currently running 14.04 I believe. Can anyone help me out here? When I run sudo apt-get update I get the below. I've tried sudo apt-get clean, apt-get autoclean, apt-get upgrade, and none are working.

When running apt-get update:
```

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease)  Unable to find expected entry 'restricted/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  Unable to find expected entry 'universe/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/gns3/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/gns3/ppa/ubuntu/dists/trusty/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/numix/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/numix/ppa/ubuntu/dists/trusty/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release](http://extras.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/Release](http://archive.canonical.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'partner/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Error after trying to upgrade to 16.x:
```

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Unable to find expected entry 'main/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease)  Unable to find expected entry 'restricted/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Unable to find expected entry 'universe/binary-[COLOR=#ff0000]**9**[/COLOR]386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Note: I've made no changes to my laptop.

Thanks!

Chaz.

---

### Post by chaz72 on 2017-01-18
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"

@[**[COLOR=#000000]Impavidus. [/COLOR]**[COLOR=#000000]No idea, but I really need this fixed. Any help is appreciated. [/COLOR]]("https://ubuntuforums.org/member.php?u=1417721")

---

### Post by ian-weisser on 2017-01-19
Please show us the complete output of the following two commands:
```
dpkg --print-architecture
dpkg --print-foreign-architectures
```

---

### Post by chaz72 on 2017-01-19
Here ya go. 9386?

cscecela@Kalibu:~$ dpkg --print-architecture
amd64
cscecela@Kalibu:~$ dpkg --print-foreign-architectures
i386
9386

---

### Post by chaz72 on 2017-01-19
9386 showed up with the foreign command and amd64 showed up with the first command. I used 
dpkg --remove-architecture 3986 then ran apt-get update and all is well. I can now launch GNS3. 

How could something like that even occur? Do I need to worry about anything else? Would an upgrade to 16.x be advised? Thank all!

---

### Post by ian-weisser on 2017-01-19
How? Cosmic rays, user typo, bad storage block, random chance. Take your pick.
Anything else? Not really.

DO NOT upgrade until you are very sure your system is functioning, and in as close-to-stock condition as possible. Upgrading a haywired or broken system usually amplifies problems instead of fixing them.
1) Backup your data. Upgrades are thoroughly tested...on somebody else's system. How much do you value your data?
2) Disable all Ubuntu sources and uninstall all non-Ubuntu software, especially upgrades from PPAs. The 'ppa-purge' application very handy for this.
3) If you removed your *buntu-desktop metapackage, reinstall it. Yes, it will reinstall some applications that you removed.
4) Test apt for function: The command 'sudo apt update && sudo apt upgrade' should return 0 packages to upgrade, and zero warnings or errors. DO NOT ignore any warnings or errors.
5) If you have an LVM or encrypted system, ensure you have adequate space on /boot

After the upgrade, you can re-implement your custom sources and applications.

---

