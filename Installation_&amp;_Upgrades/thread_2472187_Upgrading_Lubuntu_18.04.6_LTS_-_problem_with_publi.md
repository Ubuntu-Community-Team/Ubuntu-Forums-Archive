---
title: "Upgrading Lubuntu 18.04.6 LTS - problem with public key"
date: 2022-02-20
forum: Installation &amp; Upgrades
---

### Post by ianmanning on 2022-02-20
[COLOR=#232629][FONT=-apple-system]I am trying to upgrade my 18.04.6 LTS server, but am unable to get updates due to an issue with a public key. When I try to resolve the public key issue I get a failure ("[/FONT][/COLOR]keyserver receive failed: Server indicated a failure")[COLOR=#232629][FONT=-apple-system] - see below. Any ideas?
[/FONT][/COLOR]```
myuser@myuser-VirtualBox:~$ sudo apt-get update
[sudo] password for myuser: 
Hit:1 http://ppa.launchpad.net/bit-team/stable/ubuntu yakkety InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:3 http://repository.veeam.com/backup/linux/agent/dpkg/debian/public stable InRelease [7,549 B]
Hit:4 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:5 http://ppa.launchpad.net/nathan-renniewaldock/qdirstat/ubuntu yakkety InRelease
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:7 https://download.docker.com/linux/ubuntu bionic InRelease                
Get:8 https://download.docker.com/linux/ubuntu xenial InRelease [66.2 kB]    
Err:3 http://repository.veeam.com/backup/linux/agent/dpkg/debian/public stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3268CF038EEC045B
Fetched 73.8 kB in 1s (70.4 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.veeam.com/backup/linux/agent/dpkg/debian/public stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3268CF038EEC045B
W: Failed to fetch http://repository.veeam.com/backup/linux/agent/dpkg/debian/public/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3268CF038EEC045B
W: Some index files failed to download. They have been ignored, or old ones used instead.

myuser@myuser-VirtualBox:~$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 3268CF038EEC045B
Executing: /tmp/apt-key-gpghome.KcfykItU12/gpg.1.sh --keyserver hkp://keyserver.ubuntu.com:80 --recv 3268CF038EEC045B
gpg: keyserver receive failed: Server indicated a failure
```[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by Xian on 2022-02-22
Try a switch from keyserver.ubuntu.com to keys.gnupg.net in the apt-key command.

---

### Post by guiverc on 2022-02-22
Lubuntu 18.04 LTS was the *end of the road* with regards *release-upgrade* for Lubuntu.

If you note release notes on subsequent releases  ([until Lubuntu 18.04 LTS reached EOL anyway]("https://lubuntu.me/bionic-eol/")) eg. [https://lubuntu.me/focal-2-released/](https://lubuntu.me/focal-2-released/) you'll note

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

This is **not** your issue, but do NOTE your system will **not** be a *supported *one post-upgrade and you'll *possibly* experience issues with Lubuntu.

**I'd recommend** removing all Lubuntu/LXDE components, and make your system a pure Ubuntu Server install; then perform the *release-upgrade* so it'll be a supported system, then if you do actually need a desktop - you can re-add it then. That will result in a *supported* system, where as Lubuntu 18.04 LTS upgraded is not (*as it has recorded issues with regards desktop*).  

FYI: [Lubuntu 18.04 LTS also reached EOL some time ago]("https://lubuntu.me/bionic-eol/").

---

