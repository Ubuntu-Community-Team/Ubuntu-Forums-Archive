---
title: "Update problems Lubuntu 22.04"
date: 2022-05-22
forum: Installation &amp; Upgrades
---

### Post by alfredohuerta on 2022-05-22
Hi guys, I have this issue that it makes it unable to update.
Any ideas?

(base) alfredo@alfredo-hpelitebook725g4:~$ sudo apt-get update
[sudo] password for alfredo: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) impish-cran40/ InRelease                 
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish InRelease                                  
Hit:4 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable InRelease                            
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease                           
Hit:6 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                               
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates InRelease                          
Hit:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                            
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease                         
Hit:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-backports InRelease                       
Hit:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease               
Ign:12 [https://ppa.launchpadcontent.net/michael-gruz/canon/ubuntu](https://ppa.launchpadcontent.net/michael-gruz/canon/ubuntu) jammy InRelease
Err:13 [https://ppa.launchpadcontent.net/michael-gruz/canon/ubuntu](https://ppa.launchpadcontent.net/michael-gruz/canon/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/michael-gruz/canon/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by guiverc on 2022-05-22
You've added a *unsupported* or *unmaintained* PPA to your system.

PPA's are 3rd party software sources, so all security checks (*is it supported; good & supports  your release, can the owner/maintainer be trusted etc*) are on you to perform.

To me adding a [PPA that was last supported in 2011]("https://launchpad.net/~michael-gruz/+archive/ubuntu/canon") makes no sense. Did you perform any checks?

I'd just remove the PPA; as it can provide nothing useful for a *modern* system.

Lubuntu manual page appropriate : [https://manual.lubuntu.me/stable/4/4.3/software_sources.html](https://manual.lubuntu.me/stable/4/4.3/software_sources.html)

---

### Post by alfredohuerta on 2022-05-22
that ppa was the only way to actually get my Canon printer to work. For some reason seems like no one updates drivers for printers (besides HP).

---

