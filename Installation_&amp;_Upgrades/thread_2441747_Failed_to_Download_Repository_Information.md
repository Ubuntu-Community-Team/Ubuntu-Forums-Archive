---
title: "Failed to Download Repository Information"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by backspin on 2020-04-26
I want to update to Ubuntu 20.04LTS from 18.04.4LTS --  My first thought  was to check software updater, but I keep getting a strange message  about checking my Internet Connection.

[ATTACH=CONFIG]285630[/ATTACH]

I get regular updates from other bits of software that is installed and  on a regular basis, but I don't know why I'm not being notified that  20.04LTS is available.

[ATTACH=CONFIG]285629[/ATTACH]

Any thoughts about how I would go about troubleshooting this issue?

Thanks,

David

---

### Post by CelticWarrior on 2020-04-26
The main thing to understand from the error message is "failed to download repository information". The mention of internet connection is often misleading. 
The usual culprit is a PPA. Please check. Running 'sudo apt update' in terminal will show you exactly where the problem comes from.

---

### Post by deadflowr on 2020-04-26
Check with a terminal
```
sudo apt update
```
that said, waiting for the upgrade option to come is moot as upgrades from 18.04 to 20.04 aren't officially available anyway.
The official upgrade from lts to lts is always after the first point release.
(The first point release usually comes sometimes around late July/early August)

To upgrade now you need to run the updater in development mode
ie
```
update-manager -d
do-release-upgrade -d
```

---

### Post by backspin on 2020-04-26
> **CelticWarrior said:**
> The main thing to understand from the error message is "failed to download repository information". The mention of internet connection is often misleading. 
The usual culprit is a PPA. Please check. Running 'sudo apt update' in terminal will show you exactly where the problem comes from.

This is what I'm getting when running the command. looks like some kind of key problem? Or no HTTPS Certificate.. meaning it isn't secure so disabled. 


```
davidc502@Ryzen-3900x:~$ sudo apt update
[sudo] password for davidc502: 
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg
Ign:4 http://dl.google.com/linux/earth/deb stable InRelease
Hit:5 http://repo.steampowered.com/steam precise InRelease                                                           
Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                                                                     
Hit:7 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                                                                                 
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                                                               
Get:9 http://dl.google.com/linux/earth/deb stable Release [933 B]                                                                           
Get:10 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B]                                                                                              
Hit:11 http://ppa.launchpad.net/openrazer/stable/ubuntu bionic InRelease                                              
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                     
Get:13 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.7 kB]                   
Err:10 http://dl.google.com/linux/earth/deb stable Release.gpg                                            
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 78BD65473CB3BD13
Get:14 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Hit:15 http://ppa.launchpad.net/polychromatic/stable/ubuntu bionic InRelease                 
Get:16 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [301 kB]                                                          
Hit:18 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic InRelease 
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [273 kB]                                    
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]                   
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]                          
Ign:22 http://ppa.launchpad.net/sbates/ppa/ubuntu bionic InRelease                                                            
Ign:23 http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu bionic InRelease
Hit:24 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease
Err:25 http://ppa.launchpad.net/sbates/ppa/ubuntu bionic Release               
  404  Not Found [IP: 91.189.95.83 80]
Err:26 http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/earth/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 78BD65473CB3BD13
E: The repository 'http://ppa.launchpad.net/sbates/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details
```.

---

### Post by CelticWarrior on 2020-04-26
[http://ppa.launchpad.net/sbates/ppa/ubuntu](http://ppa.launchpad.net/sbates/ppa/ubuntu) is abandoned since 2015.
[http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu) is abandoned since 2012.

This ^^^ is your problem. You need to remove both repositories.
There's also an error in the Google's repo that can be fixed with:
```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 78BD65473CB3BD13
```

---

### Post by backspin on 2020-04-26
> **deadflowr said:**
> Check with a terminal
```
sudo apt update
```
that said, waiting for the upgrade option to come is moot as upgrades from 18.04 to 20.04 aren't officially available anyway.
The official upgrade from lts to lts is always after the first point release.
(The first point release usually comes sometimes around late July/early August)

To upgrade now you need to run the updater in development mode
ie
```
update-manager -d
do-release-upgrade -d
```

Ah, good to know..  as I wasn't aware.  Is it having a lot of issues right now? If so, then I probably want to stay away.

---

### Post by deadflowr on 2020-04-26
Cursory look shows that the minidnla ppa and the sbates ppa ar both unsupported (and long dead) on 18.04.
Disable those two.
As for google's pubkey issue, seems rather routine, see
[https://askubuntu.com/questions/1205540/failure-to-load-repository-information]("https://askubuntu.com/questions/1205540/failure-to-load-repository-information")

ninja'd.

---

### Post by backspin on 2020-04-26
> **CelticWarrior said:**
> [http://ppa.launchpad.net/sbates/ppa/ubuntu](http://ppa.launchpad.net/sbates/ppa/ubuntu) is abandoned since 2015.
[http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu) is abandoned since 2012.

This ^^^ is your problem. You need to remove both repositories.
There's also an error in the Google's repo that can be fixed with:
```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 78BD65473CB3BD13
```

Thanks -- Yeah, looks much better now.


```

davidc502@Ryzen-3900x:~$ sudo apt update
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg
Ign:4 http://dl.google.com/linux/earth/deb stable InRelease
Hit:5 http://repo.steampowered.com/steam precise InRelease                                                                                         
Hit:6 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                                                                                                    
Hit:7 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                                            
Get:8 http://dl.google.com/linux/earth/deb stable Release [933 B]                                                                                       
Hit:9 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                        
Get:10 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B]                                                                      
Hit:11 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                    
Hit:12 http://ppa.launchpad.net/openrazer/stable/ubuntu bionic InRelease
Hit:13 http://ppa.launchpad.net/polychromatic/stable/ubuntu bionic InRelease  
Get:14 http://dl.google.com/linux/earth/deb stable/main amd64 Packages [727 B] 
Hit:15 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic InRelease
Hit:16 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease         
Fetched 1,546 B in 1s (1,549 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'

```

---

### Post by DuckHook on 2020-04-26
> **backspin said:**
> Ah, good to know..  as I wasn't aware.  Is it having a lot of issues right now? If so, then I probably want to stay away.
If you mean by "stay away", 20.04 itself, then it's hard to say. The forums show a big uptick in users seeking help, but this happens with every launch. I would like to ask why you wish to update now? The first point release in July/August will be more stable, so if stability is more important than bright-and-shiny, you may wish to wait.

---

### Post by backspin on 2020-04-26
Much appreciate everyone's help...   I set a lot of this stuff up years ago, upgraded, and just forgot about them.  This just isn't an area that I work with very often, so I've forgotten how to handle situations like this :)

---

### Post by backspin on 2020-04-26
> **DuckHook said:**
> If you mean by "stay away", 20.04 itself, then it's hard to say. The forums show a big uptick in users seeking help, but this happens with every launch. I would like to ask why you wish to update now? The first point release in July/August will be more stable, so if stability is more important than bright-and-shiny, you may wish to wait.

Great question.  I've very please with the distro/version I'm on now as it is very stable, and I'm not having any issues.  The reason why I was thinking about upgrading was for improvements via Gui or functionality.  I've watched a few YouTube video's that talked about a few improvements I thought I might like. They aren't huge, and I'd much rather have stability than shiny and new :)   So, I think I will wait.

---

### Post by DuckHook on 2020-04-26
I opt for stability over shiny and new every time, but then, I'm old, crusty and boring.

I do have both Bionic and Focal on a dual boot, but I do so only because I help out on the forums and need at least some familiarity with the latest and greatest. If not for this consideration, I would stick with old stable versions because life is already too chaotic to go looking for more trouble.

Good Luck and Happy Ubuntu-ing!

---

