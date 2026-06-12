---
title: "trying to update but errors"
date: 2017-06-11
forum: MINT
---

### Post by devdlp on 2017-06-11
im trying to update wine because my vsts arent working in lmms so i have to do sudo apt-get update and and get this when i do:
```
deven@deven-X501A1 ~ $ sudo apt-get update
Ign:1 http://packages.linuxmint.com serena InRelease
Hit:2 http://packages.linuxmint.com serena Release                             
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Hit:7 http://repository.spotify.com stable InRelease                           
Get:8 https://repo.skype.com/deb stable InRelease [4,487 B]                    
Ign:9 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:10 https://dl.winehq.org/wine-builds/ubuntu xenial InRelease               
Hit:11 http://archive.ubuntu.com/ubuntu xenial InRelease                       
Hit:12 http://dl.google.com/linux/chrome/deb stable Release                    
Hit:13 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial InRelease        
Ign:14 http://kxstudio.linuxaudio.org/repo gcc5 InRelease                      
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]      
Ign:16 http://kxstudio.linuxaudio.org/repo stable InRelease                    
Hit:17 http://kxstudio.linuxaudio.org/repo gcc5 Release                        
Hit:18 http://kxstudio.linuxaudio.org/repo stable Release                      
Ign:8 https://repo.skype.com/deb stable InRelease                              
Get:20 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]    
Hit:23 http://download.virtualbox.org/virtualbox/debian trusty InRelease       
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
W: GPG error: https://repo.skype.com/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://download.virtualbox.org/virtualbox/debian/dists/trusty/InRelease: Signature by key 7B0FAB3A13B907435925D9C954422A4B98AB5139 uses weak digest algorithm (SHA1)
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
Moved to MINT subforum.

---

### Post by devdlp on 2017-06-11
can i please get help

---

### Post by vasa1 on 2017-06-11
Please wait for about 12 hours before asking for help on a question you just posted.> Bumping your thread if you receive no answer is acceptable. **Premature and excessive bumping could attract staff attention and action**. If you wish to bump, consider time zones - the one with your answer might be asleep.from [Posting Guidelines #14]("https://ubuntuforums.org/showthread.php?t=2158945")

---

### Post by devdlp on 2017-06-11
ok

---

### Post by oldos2er on 2017-06-11
See post #5 in this thread: [https://ubuntuforums.org/showthread.php?t=2363484](https://ubuntuforums.org/showthread.php?t=2363484)

---

### Post by devdlp on 2017-06-11
i get the same error

---

### Post by oldos2er on 2017-06-11
You still see the NO_PUBKEY error? Can you please post the full output of ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F3045A5DF7587C3
``` and ```
sudo apt update
```

---

