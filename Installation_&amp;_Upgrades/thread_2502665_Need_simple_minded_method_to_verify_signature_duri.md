---
title: "Need simple minded method to verify signature during dist upgrade"
date: 2024-11-23
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2024-11-23
I'm upgrading from 20.04 to 22.04. I performed this on a test install and it went without a hitch. Now I am doing it on my daily system and I get the following result at the "$ sudo apt update && sudo apt dist-upgrade" stage...
```
  Inspiron-660:~$ sudo apt update && sudo apt dist-upgrade
[sudo] password for daryl: 
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Get:2 http://dl.google.com/linux/earth/deb stable InRelease [1,821 B]          
Hit:3 http://ca.archive.ubuntu.com/ubuntu focal InRelease                      
Hit:4 http://ca.archive.ubuntu.com/ubuntu focal-updates InRelease              
Hit:5 http://ca.archive.ubuntu.com/ubuntu focal-backports InRelease            
Hit:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal InRelease
Get:7 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease [1,560 B]
Err:2 http://dl.google.com/linux/earth/deb stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E88979FB9B30ACF2
Err:7 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0FAD31CA8719FCE4
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/earth/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E88979FB9B30ACF2
W: GPG error: http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0FAD31CA8719FCE4
E: The repository 'http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
 
```
  
I'm stumped as to how to handle this. Please give me step by step method.

---

### Post by grahammechanical on 2024-11-24
First thing. Are you aware the dist-upgrade does not upgrade to the next release of Ubuntu? See the the man page

```
man apt-get
```

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

It can break th7ings.

Second. Open Software and Updates>Other Software tab and disable those two software sources. That is, opensuse and dl.google. It will also the sensible to disable any PPAs such as yannubuntu even though it is not throwing up an error. 

Try re-enabling them after the upgrade to the next version of Ubuntu.

Regards

---

### Post by him610 on 2024-11-25
```
Err:2 http://dl.google.com/linux/earth/deb stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E88979FB9B30ACF2
Err:7 http://download.[COLOR="#FF0000"]opensuse[/COLOR].org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0FAD31CA8719FCE4
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/earth/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E88979FB9B30ACF2
W: GPG error: http://download.[COLOR="#FF0000"]opensuse[/COLOR].org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0FAD31CA8719FCE4
E: The repository 'http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_20.04  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default. 
```
Looks like you have some fragments of previous *opensuse *installation. Maybe you should eliminate those fragments followed up with...
```

sudo apt update
sudo apt autoremove
sudo apt upgrade
man apt (shows apt options)

```

---

### Post by ian-weisser on 2024-11-25
The title is misleading.

The problem is not that you need to verify signatures. Apt does that automatically anyway.
The problem is that you are using non-Ubuntu sources with missing or invalid signatures that failed verification.

Best practice is to disable all non-Ubuntu sources and uninstall all non-Ubuntu software from those sources before starting a release-upgrade anyway.
Return your system to as close to stock condition as possible for the highest probability of success with a release-upgrade.
Non-Ubuntu packages and non-Ubuntu sources are the #1 cause of broken release-upgrades. Including, apparently, yours.

---

