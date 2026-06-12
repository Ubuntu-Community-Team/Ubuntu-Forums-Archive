---
title: "lubuntu ppa 404"
date: 2019-05-23
forum: Installation &amp; Upgrades
---

### Post by carmello6769 on 2019-05-23
Hi All,

I just did a lubuntu install yesterday and while making sure that everything was up to date I got this error:

carmen@carmen-pc:~$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-updates InRelease [97.5 kB]                            
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-backports InRelease                                    
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease [97.5 kB]
Ign:5 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) disco InRelease
Err:6 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) disco Release              
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Did I get an out of date repository with my install or is there another issue. Thanks in advance!

---

### Post by CatKiller on 2019-05-23
That url resolves for me. Possibly a dns issue or temporary Internet hiccup?

Although looking deeper, there isn't an entry for disco, since that ppa doesn't seem to have been updated since 2015.

---

### Post by Frogs Hair on 2019-05-23
The PPA appears to be outdated. You should be able to remove it from your software sources list. In Ubuntu that is located in software and updates/other software though it may different on Lubuntu/LXQT. 


[https://launchpad.net/~lubuntu-desktop/+archive/ubuntu/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ubuntu/ppa)

---

### Post by carmello6769 on 2019-05-23
Thanks for the help everyone. Weird that an outdated ppa would be included in the latest version of the distro.. I'm just curious if there is one that's lubuntu specific that replaces it.

---

### Post by Frogs Hair on 2019-05-23
I've never heard of an official Ubuntu distro with a ppa included and I've tried most with the exception of Lubuntu. Where did you download from? 

 [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by oldos2er on 2019-05-23
> **carmello6769 said:**
>  Weird that an outdated ppa would be included in the latest version of the distro.

No PPAs are included in any Ubuntu flavor that I'm aware of.

---

