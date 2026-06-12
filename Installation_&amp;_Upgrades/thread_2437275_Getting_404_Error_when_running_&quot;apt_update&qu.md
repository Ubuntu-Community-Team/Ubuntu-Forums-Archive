---
title: "Getting 404 Error when running &quot;apt update&quot; on 18.10"
date: 2020-02-20
forum: Installation &amp; Upgrades
---

### Post by phu004 on 2020-02-20
Hi guys, 

I was trying to upgrade my 64 bits ubuntu 18.10 to 19.04. However, When i run "sudo apt update" command on the terminal, I got error messages that seem to suggest there is something wrong with the repository.
Can any one help me what the problem could be?

Thanks in advance!

```

Hit:1 http://packages.microsoft.com/repos/vscode stable InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                              
Hit:3 http://archive.canonical.com/ubuntu cosmic InRelease                                                                                                
Ign:4 http://ppa.launchpad.net/aims/sagemath/ubuntu cosmic InRelease                                                  
Ign:5 http://archive.ubuntu.com/ubuntu cosmic InRelease                                                                   
Get:6 http://dl.google.com/linux/chrome/deb stable Release [943 B]                             
Get:7 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]   
Err:7 http://dl.google.com/linux/chrome/deb stable Release.gpg                 
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 78BD65473CB3BD13
Ign:8 http://archive.ubuntu.com/ubuntu cosmic-updates InRelease          
Hit:9 http://ppa.launchpad.net/linuxuprising/java/ubuntu cosmic InRelease
Ign:10 http://archive.ubuntu.com/ubuntu cosmic-backports InRelease                                  
Ign:11 http://archive.ubuntu.com/ubuntu cosmic-security InRelease        
Hit:12 http://ppa.launchpad.net/webupd8team/java/ubuntu cosmic InRelease
Err:13 http://archive.ubuntu.com/ubuntu cosmic Release                                               
  404  Not Found [IP: 91.189.88.24 80]
Err:14 http://archive.ubuntu.com/ubuntu cosmic-updates Release           
  404  Not Found [IP: 91.189.88.24 80]
Err:15 http://ppa.launchpad.net/aims/sagemath/ubuntu cosmic Release
  404  Not Found [IP: 91.189.95.83 80]
Err:16 http://archive.ubuntu.com/ubuntu cosmic-backports Release
  404  Not Found [IP: 91.189.88.24 80]
Err:17 http://archive.ubuntu.com/ubuntu cosmic-security Release
  404  Not Found [IP: 91.189.88.24 80]
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/chrome/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 78BD65473CB3BD13
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/aims/sagemath/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu cosmic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by Frogs Hair on 2020-02-20
18.10 is no longer supported. It would be best to install a supported release. see the linked wiki.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Impavidus on 2020-02-21
19.04 reached end of life too. I don't recommend a double end-of-life upgrade. Try a fresh install.

---

