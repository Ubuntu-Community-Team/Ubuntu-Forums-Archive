---
title: "error of ssh installation"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by linux_sky on 2011-07-07
hello, when i run "sudo apt-get install ssh", i have this error returned:-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ssh
0 upgraded, 1 newly installed, 0 to remove and 176 not upgraded.
Need to get 1,280 B of archives.
After this operation, 41.0 kB of additional disk space will be used.
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) natty/main ssh all 1:5.8p1-1ubuntu3
  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_5.8p1-1ubuntu3_all.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_5.8p1-1ubuntu3_all.deb)  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


may i know how can i fix it? thank you

---

### Post by kronick on 2011-07-07
it seems to me that it cant connect to [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com)

EDIT 1: Although i can access it with no problem, so this is weird, did you try running

```
sudo apt-get update
```

try adding another mirror to sources.list

---

### Post by linux_sky on 2011-07-07
> **kronick said:**
> it seems to me that it cant connect to [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com)

EDIT 1: Although i can access it with no problem, so this is weird, did you try running

```
sudo apt-get update
```

try adding another mirror to sources.list

i try to run the command you gave me, it did not work



Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                  
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) natty InRelease                                                              
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) natty-updates InRelease                                                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                                                      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                           
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) natty Release.gpg                                                             
  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                               
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) natty-updates Release.gpg                                                     
  Something wicked happened resolving 'my.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources/DiffIndex                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources/DiffIndex                
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) natty Release                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources/DiffIndex                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages/DiffIndex          
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) natty-updates Release                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources/DiffIndex                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex

---

### Post by linux_sky on 2011-07-12
case closed. already fixed but setting network on virtual box.

---

