---
title: "Unable to Install Updates"
date: 2022-04-25
forum: Installation &amp; Upgrades
---

### Post by megtechnica on 2022-04-25
Hello, 
I am unable to install some updates and need some help.  After running sudo apt-get update, I receive the following.  
Please advise.  

```
[FONT=monospace][COLOR=#000000]Ign:1 http://us.archive.ubuntu.com/ubuntu disco InRelease                                                                                                                 [/COLOR]
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                              
Get:3 http://repository.spotify.com stable InRelease [3,316 B]                                                                                      
Ign:4 http://security.ubuntu.com/ubuntu disco-security InRelease                                                                                                
Hit:5 https://updates.signal.org/desktop/apt xenial InRelease                                                                 
Ign:6 http://us.archive.ubuntu.com/ubuntu disco-updates InRelease                                       
Get:7 https://download.docker.com/linux/ubuntu disco InRelease [44.4 kB]                                
Ign:8 http://us.archive.ubuntu.com/ubuntu disco-backports InRelease                                            
Err:3 http://repository.spotify.com stable InRelease                                                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5E3C45D7B312C643
Err:9 http://security.ubuntu.com/ubuntu disco-security Release                                                      
  404  Not Found [IP: 2620:2d:4000:1::16 80]
Err:10 http://us.archive.ubuntu.com/ubuntu disco Release                                                            
  404  Not Found [IP: 91.189.91.38 80]
Err:11 http://us.archive.ubuntu.com/ubuntu disco-updates Release
  404  Not Found [IP: 91.189.91.38 80]
Err:12 http://us.archive.ubuntu.com/ubuntu disco-backports Release                    
  404  Not Found [IP: 91.189.91.38 80]
Ign:13 http://apt.postgresql.org/pub/repos/apt disco-pgdg InRelease                   
Err:14 http://apt.postgresql.org/pub/repos/apt disco-pgdg Release
  404  Not Found [IP: 2604:1380:2000:7501::69 80]
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.spotify.com stable I
nRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5E3C45D7B312C643
E: The repository 'http://security.ubuntu.com/ubuntu disco-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu disco Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu disco-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu disco-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://apt.postgresql.org/pub/repos/apt disco-pgdg Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

[/FONT]
```

---

### Post by deadflowr on 2022-04-25
Ubuntu 19.04 Disco Dingo is no longer supported and the archives have been removed.
Please install a supported release.
You've marked this thread with the kde prefix so I'm guessing you would want Kubuntu.
You can go here: [https://kubuntu.org/getkubuntu/]("https://kubuntu.org/getkubuntu/")
to get the any of latest Kubuntu's currently supported releases.

---

