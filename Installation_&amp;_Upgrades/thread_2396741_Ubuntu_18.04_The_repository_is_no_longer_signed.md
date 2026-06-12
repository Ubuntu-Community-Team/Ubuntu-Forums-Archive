---
title: "Ubuntu 18.04 The repository is no longer signed"
date: 2018-07-20
forum: Installation &amp; Upgrades
---

### Post by sunnixx on 2018-07-20
Hi

I am getting this error when ever I am trying to ```
sudo apt-get update
```

```
[FONT=monospace][COLOR=#000000]Get:1 http://pk.archive.ubuntu.com/ubuntu bionic InRelease [253 B][/COLOR]
Err:1 http://pk.archive.ubuntu.com/ubuntu bionic InRelease                                                                                           
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                                                    
Hit:3 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease                                                                              
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                         
Get:5 http://pk.archive.ubuntu.com/ubuntu bionic-updates InRelease [261 B]                                                                           
Err:5 http://pk.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                   
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Hit:6 https://download.mono-project.com/repo/ubuntu stable-bionic InRelease                                                                          
Get:7 http://pk.archive.ubuntu.com/ubuntu bionic-backports InRelease [263 B]                                                                         
Err:7 http://pk.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                                 
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Hit:8 http://packages.microsoft.com/repos/vscode stable InRelease                                                                                    
Hit:9 https://dl.yarnpkg.com/debian stable InRelease                                                                                                 
Hit:10 http://dl.google.com/linux/chrome/deb stable Release                                                                                          
Hit:12 https://packages.microsoft.com/ubuntu/18.04/prod bionic InRelease                                                                             
Hit:13 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease                   
Reading package lists... Done  
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://pk.archive.ubuntu.com/ubuntu bionic InRelease' is no longer signed.
E: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/bionic/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require 
authentication?)
E: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network 
require authentication?)
E: The repository 'http://pk.archive.ubuntu.com/ubuntu bionic-updates InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://pk.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the networ
k require authentication?)
E: The repository 'http://pk.archive.ubuntu.com/ubuntu bionic-backports InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

[/FONT]
```

Any help would be really appreciated ?

---

### Post by TheFu on 2018-07-20
If you visit [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) with a normal browser, what happens?

---

### Post by sunnixx on 2018-07-21
I can access it properly and even ```
wget
``` returns me with success

---

