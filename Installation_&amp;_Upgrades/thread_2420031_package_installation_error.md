---
title: "package installation error"
date: 2019-05-29
forum: Installation &amp; Upgrades
---

### Post by rcrahul60 on 2019-05-29
i upgraded to ubuntu 19.04 and it seems like it doesn't support architecture i386. i don't know much about this but its means it doesn't support 32 bit. but i have 64 bit os so it should not be causing any problem. it also crashes multiple times like while starting it just keep looping on ubuntu logo btw here my error:

[HTML]tbosss@tbosss-550P5C-550P7C:~$ sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils
Hit:1 http://security.ubuntu.com/ubuntu disco-security InRelease
Hit:2 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu disco InRelease     
0% [Waiting for headers] [Connecting to ppa.launchpad.net (91.189.95.83)] [Conn
Hit:3 http://in.archive.ubuntu.com/ubuntu disco InRelease                      
Ign:4 http://ppa.launchpad.net/relan/exfat/ubuntu disco InRelease              
Hit:5 http://in.archive.ubuntu.com/ubuntu disco-updates InRelease   
Hit:6 http://apt.postgresql.org/pub/repos/apt disco-pgdg InRelease       
Hit:7 http://in.archive.ubuntu.com/ubuntu disco-backports InRelease      
Err:8 http://ppa.launchpad.net/relan/exfat/ubuntu disco Release          
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/relan/exfat/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://apt.postgresql.org/pub/repos/apt disco-pgdg InRelease' doesn't support architecture 'i386'
[/HTML]

---

### Post by kc1di on 2019-05-29
this PPA ```
The repository 'http://ppa.launchpad.net/relan/exfat/ubuntu disco
```
does not yet have a disco release repository so it will not upgrade from it.   You will have to disable it for now. 

Go to software and updates then other tab and uncheck this ppa for now.

---

