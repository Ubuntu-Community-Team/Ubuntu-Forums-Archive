---
title: "Upgrade issues"
date: 2024-09-22
forum: Installation &amp; Upgrades
---

### Post by david.gurnett on 2024-09-22
I clicked on the dialogue to upgrade software and it successfully did this. It then asked me to restart Ubuntu, which I did. However I now have the contents/folders of my Home folder displayed on my desktop. I don't want this. How do I get rid of it? Has anyone else had this problem?

---

### Post by grahammechanical on 2024-09-23
It would help if you told us what version of Ubuntu you are using. Are you using Ubuntu? Or are you using another Linux distribution. On the more modern versions of Ubuntu to put icons on the desktop we need to install a Gnome extension. 

Ubuntu developers have create their own Gnome extension that is installed by default. But that will only put an icon of the home folder on the desktop and also the rubbish bin icon. Although in Ubuntu 24.10 the rubbish bin icon in on the dock. The contents of the home folder are not put on the desktop.

Regards

---

### Post by ActionParsnip on 2024-09-24
What is the full output of
```

sudo apt update
sudo apt -f install

```
Thanks

---

### Post by yancek on 2024-09-24
Providing the information requested in the posts above would be a good first step.  If you are using a standard, default Ubuntu with Gnome and Nautilus, this should not happen.  In fact, there are numerous posts on this forum from members who are trying to get icons on their Desktop and are unable to do so. Getting Desktop icons when using Gnome/Nautilus is a rather convoluted multi-step process so post more details.

---

### Post by david.gurnett on 2024-09-24
This is the output:

```
Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble InRelease
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-updates InRelease [126 kB]     
Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-backports InRelease            
Get:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-updates/main amd64 Packages [530 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-updates/main Translation-en [128 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-updates/main amd64 c-n-f Metadata [8,564 B]
Get:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-updates/universe amd64 Packages [374 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) noble-updates/universe i386 Packages [162 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease [126 kB]      
Hit:10 [https://ppa.launchpadcontent.net/kdenlive/kdenlive-stable/ubuntu](https://ppa.launchpadcontent.net/kdenlive/kdenlive-stable/ubuntu) noble InRelease
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 Packages [377 kB]
Hit:12 [https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu](https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu) noble InRelease
Ign:13 [https://ppa.launchpadcontent.net/scribus/ppa/ubuntu](https://ppa.launchpadcontent.net/scribus/ppa/ubuntu) noble InRelease
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main Translation-en [81.6 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security/main amd64 c-n-f Metadata [4,528 B]
Err:16 [https://ppa.launchpadcontent.net/scribus/ppa/ubuntu](https://ppa.launchpadcontent.net/scribus/ppa/ubuntu) noble Release       
  404  Not Found [IP: 185.125.190.80 443]
Reading package lists... Done
W: [https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu/dists/noble/InRelease:](https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu/dists/noble/InRelease:) Signature by key FBA0C227099A5360635E3D9152165BD6B9BA26FA uses weak algorithm (rsa1024)
E: The repository 'https://ppa.launchpadcontent.net/scribus/ppa/ubuntu noble Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

---

### Post by david.gurnett on 2024-09-24
I'm using the current version of Ubuntu, stock standard, no additions or extensions. It appears to be working fine. I just want to get the icons off my desktop.

---

### Post by deadflowr on 2024-09-25
> W: [https://ppa.launchpadcontent.net/ope...ble/InRelease:](https://ppa.launchpadcontent.net/ope...ble/InRelease:) Signature by key FBA0C227099A5360635E3D9152165BD6B9BA26FA uses weak algorithm (rsa1024)
E: The repository 'https://ppa.launchpadcontent.net/scribus/ppa/ubuntu noble Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Disable and remove the scribus ppa as it doesn't support noble.

The warning message for the openshot ppa should have a fix as they've updated all the keys on launchpad to a higher version, 
I think they're all at least rsa2048 now, maybe rsa4096.
Might require a quick add-apt-repository --remove and then re-add it.
(There is supposed to be some tool to make it so you don't need to remove and re-add the ppa but I don't know what it is)
More here: [https://discourse.ubuntu.com/t/new-requirements-for-apt-repository-signing-in-24-04/42854](https://discourse.ubuntu.com/t/new-requirements-for-apt-repository-signing-in-24-04/42854)
> I just want to get the icons off my desktop.
Settings > Ubuntu Desktop should have toggle to turn off Desktop icons.
And also move any files inside the Desktop folder in Files to another location.
.

---

