---
title: "update errors"
date: 2021-08-03
forum: Installation &amp; Upgrades
---

### Post by aps94 on 2021-08-03
Hello, I am relatively new to Linux and wanted to give it go. I have installed it and done some basic commands in the terminal and got some software installed (which is wonderful) however I now have an issue. 

I had not used this Linux machine for a few months and when I started it up and checked for updates via sudo apt-get update I get this error:

```
Ign:1 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) hirsute InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute-updates InRelease      
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute-backports InRelease [101 kB]
Err:5 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) hirsute Release        
  404  Not Found [IP: 91.189.95.85 80]
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hirsute InRelease                 
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hirsute-security InRelease [101 kB]
Reading package lists... Done      
E: The repository 'http://ppa.launchpad.net/teejee2008/ppa/ubuntu hirsute Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I am not sure how to go about fixing this. Is this just a message to say that there are no updates or the new update is incompatible with my Linux distribution?

I am running Ubuntu 21.04
GNOME Version 3.38.5

I get the feeling this is a really easy fix and I am completely missing something but I appreciate all the help I can get.
Thank you!!

---

### Post by deadflowr on 2021-08-03
Disable the teejee2008 ppa as there are no hirsute archives in it.
The only package the ppa maintainers has built for hirsute is timeshift which is in it's own separate ppa:
[https://launchpad.net/~teejee2008/+archive/ubuntu/timeshift]("https://launchpad.net/~teejee2008/+archive/ubuntu/timeshift")

---

### Post by aps94 on 2021-08-03
> **deadflowr said:**
> Disable the teejee2008 ppa as there are no hirsute archives in it.
The only package the ppa maintainers has built for hirsute is timeshift which is in it's own separate ppa:
[https://launchpad.net/~teejee2008/+archive/ubuntu/timeshift](https://launchpad.net/~teejee2008/+archive/ubuntu/timeshift)

Thank you, I will get to doing that and report back if I get it working or not!

---

### Post by ActionParsnip on 2021-08-03
The PPA doesn't support your release of Ubuntu. Not all PPAs support all releases and it should be removed

---

### Post by aps94 on 2021-08-03
Reporting back, this was the case, thank you ever so much for your help. It never occured to me to try that. I was scratching my head, surfing the web and trying to work this out and it really was as simple as that!

---

