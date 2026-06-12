---
title: "Package Manager Error #2"
date: 2019-09-14
forum: Installation &amp; Upgrades
---

### Post by perkanator on 2019-09-14
Hello,

I am getting a package manager error, I need help

```
sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Hit:4 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Fetched 163 kB in 1s (179 kB/s)    
Segmentation fault (core dumped)
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code

```

---

