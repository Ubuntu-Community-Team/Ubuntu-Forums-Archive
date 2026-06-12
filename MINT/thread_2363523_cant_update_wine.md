---
title: "cant update wine"
date: 2017-06-11
forum: MINT
---

### Post by devdlp on 2017-06-11
i cant update wine something is really wrong look.
```
deven@deven-X501A1 ~ $ sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main'
[sudo] password for deven: 
deven@deven-X501A1 ~ $ sudo apt-get update
Ign:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) serena InRelease
Hit:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) serena Release                             
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:6 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial InRelease
Hit:7 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Get:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease [4,487 B]                    
Ign:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:10 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease               
Hit:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                       
Hit:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Hit:13 [http://ppa.launchpad.net/ricotz/unstable/ubuntu](http://ppa.launchpad.net/ricotz/unstable/ubuntu) xenial InRelease        
Ign:14 [http://kxstudio.linuxaudio.org/repo](http://kxstudio.linuxaudio.org/repo) gcc5 InRelease                      
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]      
Ign:16 [http://kxstudio.linuxaudio.org/repo](http://kxstudio.linuxaudio.org/repo) stable InRelease                    
Hit:17 [http://kxstudio.linuxaudio.org/repo](http://kxstudio.linuxaudio.org/repo) gcc5 Release                        
Hit:18 [http://kxstudio.linuxaudio.org/repo](http://kxstudio.linuxaudio.org/repo) stable Release                      
Ign:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]    
Hit:23 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty InRelease       
Fetched 209 kB in 5s (38.7 kB/s)          
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: GPG error: [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://download.virtualbox.org/virtualbox/debian/dists/trusty/InRelease:](http://download.virtualbox.org/virtualbox/debian/dists/trusty/InRelease:) Signature by key 7B0FAB3A13B907435925D9C954422A4B98AB5139 uses weak digest algorithm (SHA1)
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:2
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:1 and /etc/apt/sources.list.d/additional-repositories.list:3
deven@deven-X501A1 ~ $
```

---

### Post by vasa1 on 2017-06-11
Please learn to use code tags. Read this carefully: [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by jeremy31 on 2017-06-11
```
sudo apt-get update && curl https://repo.skype.com/data/SKYPE-GPG-KEY | sudo apt-key add - 
```
Should fix the skype key error and post results for ```
inxi -r
```

---

### Post by howefield on 2017-06-11
For the Skype error try..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F3045A5DF7587C3
```

The Virtualbox error should not be fatal as I understand it.

Edit : ninja'ed :)

---

