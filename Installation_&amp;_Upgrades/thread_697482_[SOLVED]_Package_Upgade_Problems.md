---
title: "[SOLVED] Package Upgade Problems"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by tommohawk on 2008-02-15
Hi, I am having a problem installing system updates on my Gutsy system.

Every time the system tries to update it comes up with this error

> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

and another error like this for every repository in my index.

The update manager runs correctly and tells me that there are currently 51 updates to install but just keeps giving me this error (for 3 days now)

Nothing has been altered on my system, the networking setup is exactly the same as it was and the router settings are all the same.

It's no doubt a simple fix but I just can't find it!!

---

### Post by Pumalite on 2008-02-15
Post:
uname -a

---

### Post by tommohawk on 2008-02-15
> **Pumalite said:**
> Post:
uname -a

```
Linux ken-laptop 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

```

---

### Post by Pumalite on 2008-02-15
Funny. I just updated to 14-52 and had no problems. I don't understand why you are getting 52_i386 when you run a 14-generic-i686. Check your sources list and your connection Do you have the i386 kernel in your Grub menu?

---

### Post by tommohawk on 2008-02-15
> **Pumalite said:**
> Funny. I just updated to 14-52 and had no problems. I don't understand why you are getting 52_i386 when you run a 14-generic-i686. Check your sources list and your connection Do you have the i386 kernel in your Grub menu?

Hi, this is my sources.list file.  Ignore the mint repository it was only added so I could use the linux mint menu because it is better than the ubuntu system panel.

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

#AUTOMATIX REPOS END
# deb http://www.linuxmint.com/repository daryna/
deb http://www.virtualbox.org/debian gutsy non-free

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://apt.mediatomb.cc/ feisty main
deb http://www.geexbox.org/debian/ unstable main
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

As for grub, I only have 22-14 generic kernels listed.

I can't see a problem with the sources file either - it hasn't been changed for months.

---

### Post by Pumalite on 2008-02-15
What is this?:
'deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted'
I would put some order. You have Gutsy and Feisty.

---

### Post by tommohawk on 2008-02-15
thats the original install CD, don't ask how it is now all i686 I don't really understand that bit.  I am running a centrino dual core if that explains that bit.

As for the reference to feisty, thast is only in relation to mediatomb and only because there was no gutsy repository available.

---

### Post by Pumalite on 2008-02-15
Comment out (#) the line:
deb cdrom...blah...blah
Then try again.

---

### Post by tommohawk on 2008-02-15
Nope, no difference.

To me the problem looks network related as it mentions the problem with a connection to the local host.

Interestingly enough, the system update notification came on 3 days ago saying there were 41 updates available, then 46 and today 51 so the repository information must be being read somehow.

I have no other network issues, email and web browsing works fine, so does other types of download.  It is just this....

---

### Post by Pumalite on 2008-02-15
I gather you have a router providing you with DHCP.
Post:
lshw -C network

---

### Post by tommohawk on 2008-02-15
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:41:d5:14
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.99 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:30:8c:c8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vbox0
       serial: 00:ff:00:1e:55:20
       size: 10MB/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A link=no multicast=yes port=twisted pair speed=10MB/s

```

---

### Post by Pumalite on 2008-02-15
Are you sure your wireless connection is OK.?

---

### Post by tommohawk on 2008-02-15
Well mostly yes.  It is the connection I am using now.

However,  I often have to input the security key multiple times before it connects.  Don't have the problem in windows, only in ubuntu.  As ubuntu is my primary OS, I need that connection to be stable.

---

### Post by tommohawk on 2008-02-16
Tried again this morning - still the same problem.

---

### Post by zvacet on 2008-02-16
Try to put # in front of automatix line and save file.In sysem>admin<software sources select main server.

---

### Post by tommohawk on 2008-02-16
> **zvacet said:**
> Try to put # in front of automatix line and save file.In sysem>admin<software sources select main server.

Tried that before but not the automatix bit.

Tried again today but no luck.  When trying to update the repository index I get this:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

and then a list of the same errors saying cannot connect to localhost.

```
http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://www.virtualbox.org/debian/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://www.virtualbox.org/debian/dists/gutsy/non-free/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://apt.mediatomb.cc/dists/feisty/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://apt.mediatomb.cc/dists/feisty/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://www.geexbox.org/debian/dists/unstable/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://www.geexbox.org/debian/dists/unstable/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

I think this is going down the wrong route - I am convinced it is a problem with my network somewhere but I can't understand why I am not having problems with any other network related functions.

---

### Post by Pumalite on 2008-02-16
Get wired to the Internet while upgrading. Get DHCP.

---

### Post by tommohawk on 2008-02-16
Sorted!

The problem was down to the installation of the anon-proxy package.  Once I had completely removed that and privoxy, done a reboot, everything was fine.

It's a learning point!

---

### Post by Pumalite on 2008-02-16
Yes, indeed. Gongrats.

---

### Post by LaoziSailor on 2008-02-27
> **tommohawk said:**
> Sorted!

The problem was down to the installation of the anon-proxy package.  Once I had completely removed that and privoxy, done a reboot, everything was fine.

It's a learning point!

Amazing stroke of luck for me. This one hit the nail right on the head even though my problem was slightly different.

Thanks!

---

