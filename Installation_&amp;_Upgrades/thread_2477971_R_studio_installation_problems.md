---
title: "R studio installation problems"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by yoshiki2 on 2022-08-13
I am having error after trying to install Rstudio.
Any ideas?

(base) alfredo@alfredo-hpelitebook725g4:~$ sudo apt update && sudo apt upgrade
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease                          
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease                        
Hit:4 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) jammy InRelease                                     
Hit:5 [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu) jammy-cran40/ InRelease                 
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                           
Hit:7 [https://packages.microsoft.com/repos/edge](https://packages.microsoft.com/repos/edge) stable InRelease                           
Hit:8 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease             
Hit:9 [https://ppa.launchpadcontent.net/lubuntu-dev/backports/ubuntu](https://ppa.launchpadcontent.net/lubuntu-dev/backports/ubuntu) jammy InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: [http://repo.mysql.com/apt/ubuntu/dists/jammy/InRelease:](http://repo.mysql.com/apt/ubuntu/dists/jammy/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 rstudio : Depends: libssl1.0.0 but it is not installable or
                    libssl1.0.2 but it is not installable or
                    libssl1.1 but it is not installable
           Depends: libclang-dev but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by yancek on 2022-08-13
>  Unmet dependencies. Try 'apt --fix-broken install' with no packages

What happened when you ran the command suggested above?

---

