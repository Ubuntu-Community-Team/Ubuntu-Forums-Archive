---
title: "I upgraded from 20.04 LTS to 22.04 LTS and messed up!"
date: 2022-07-26
forum: Installation &amp; Upgrades
---

### Post by nkg47 on 2022-07-26
I upgraded my system today from 20.04 LTS to 22.04 LTS, and changed the repositories and turns out that my apt update and apt upgrade outputs are flooded with warnings and errors. I need help as I have tried my best and whatever I try to do seems to break up the system even more. Here are the details from the terminal:


[FONT=book antiqua]mahadev@mahadev-Lenovo-G580:~$ sudo apt update && sudo apt upgrade && sudo apt autoremove
Hit:1 [https://download.onlyoffice.com/repo/debian](https://download.onlyoffice.com/repo/debian) squeeze InRelease
Hit:2 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease                                                                                
Hit:3 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable InRelease                                                                                      
Err:1 [https://download.onlyoffice.com/repo/debian](https://download.onlyoffice.com/repo/debian) squeeze InRelease                                                                                  
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8320CA65CB2DE8E5
Hit:4 [http://deb.fdmpkg.org](http://deb.fdmpkg.org) bionic InRelease                                                                                                         
Hit:5 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                                                                                              
Hit:6 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) preview InRelease                                                                                             
Hit:7 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                                                                                          
Hit:8 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                                                   
Hit:9 [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) jammy InRelease                           
Hit:10 [http://deb.volian.org/volian](http://deb.volian.org/volian) scar InRelease                  
Hit:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Err:4 [http://deb.fdmpkg.org](http://deb.fdmpkg.org) bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 38832685B6D09383
Err:5 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Err:6 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) preview InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease [99.8 kB]
Err:7 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5E3C45D7B312C643
Hit:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease
Fetched 99.8 kB in 3s (37.4 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://download.onlyoffice.com/repo/debian](https://download.onlyoffice.com/repo/debian) squeeze InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8320CA65CB2DE8E5
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.fdmpkg.org](http://deb.fdmpkg.org) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 38832685B6D09383
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) preview InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5E3C45D7B312C643
W: Failed to fetch [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5E3C45D7B312C643
W: Failed to fetch [http://deb.fdmpkg.org/dists/bionic/InRelease](http://deb.fdmpkg.org/dists/bionic/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 38832685B6D09383
W: Failed to fetch [https://download.onlyoffice.com/repo/debian/dists/squeeze/InRelease](https://download.onlyoffice.com/repo/debian/dists/squeeze/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8320CA65CB2DE8E5
W: Failed to fetch [https://linux.teamviewer.com/deb/dists/stable/InRelease](https://linux.teamviewer.com/deb/dists/stable/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
W: Failed to fetch [https://linux.teamviewer.com/deb/dists/preview/InRelease](https://linux.teamviewer.com/deb/dists/preview/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]



Please help me with this. Thanks in advance :)

---

### Post by coffeecat on 2022-07-26
Duplicate of [https://ubuntuforums.org/showthread.php?t=2477475](https://ubuntuforums.org/showthread.php?t=2477475)

Thread closed.

---

