---
title: "No Updates to 18.04 for the last week"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by castlefox on 2018-05-02
Hello,

I installed Ubuntu 18.04 last Friday and I dont think I have received any updates after that initial install.   Normally I would expect like some updates like on a daily basis since its a new release.... Where/how do I check what updates I should be getting?    Maybe I am missing something.  Just doesnt feel like its supposed to be working like its supposed to. 

Thanks

---

### Post by Xian on 2018-05-02
Let's take a look. &#128064;

Can you post the contents of your /etc/apt/sources.list file?

---

### Post by monkeybrain20122 on 2018-05-02
> **castlefox said:**
> Hello,

I installed Ubuntu 18.04 last Friday and I dont think I have received any updates after that initial install.   Normally I would expect like some updates like on a daily basis since its a new release.... Where/how do I check what updates I should be getting?    Maybe I am missing something.  Just doesnt feel like its supposed to be working like its supposed to. 

Thanks

I think it is kind of normal. Updates are rapid and massive on a daily basis towards release and then once release is official updates stops or slows down considerably over the next few weeks, It is my experience with all releases in the past. If in your initial install you checked install updates then there is no more update after that.

---

### Post by Dennis N on 2018-05-03
Security updates are set to be automatically downloaded and installed. So you would not notice them. Other updates are set to show only weekly.
Those are the default settings. You can change the settings of course in Software and Updates tool.

---

### Post by Skaperen on 2018-05-03
yes, they stop updates for a while so everyone who wants to run 18.04 (not me) is on the same exact version so that reports of issues are consistent.  critical security updates are probably an exception.  IMHO, they should insert a daily dummy package install (just update a file with the date) so that people can verify they a configured correctly to get real updates when they are ready.

---

### Post by marcoslai2 on 2018-05-03
Whenever I tried to update,it show **'Failed to download repository information. Check your connection.' **My connection is good,I wonder what goes wrong.

---

### Post by Dennis N on 2018-05-03
> **marcoslai2 said:**
> Whenever I tried to update,it show **'Failed to download repository information. Check your connection.' **My connection is good,I wonder what goes wrong.

Post the output of:
```
sudo apt-get update
```
This should reveal any repository that is causing the problem.

---

### Post by castlefox on 2018-05-03
> **Xian said:**
> Let's take a look. &#55357;&#56384;

Can you post the contents of your /etc/apt/sources.list file?

This is what is in my file>

```
#deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse 
```

---

### Post by marcoslai2 on 2018-05-03
This is the output :

```
Ign:1 [http://security.debian.org/debian-security](http://security.debian.org/debian-security) bionic InRelease                                                                             
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                                                                                       
Err:3 [http://security.debian.org/debian-security](http://security.debian.org/debian-security) bionic Release                               
  404  Not Found [IP: 2a04:4e42:2::204 80]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [65.4 kB]                     
Ign:5 [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) bionic InRelease   
Ign:6 [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) bionic-updates InRelease
Err:7 [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) bionic Release                     
  404  Not Found [IP: 2600:3402:200:227::2 80]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease [69.9 kB]
Err:9 [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) bionic-updates Release
  404  Not Found [IP: 2600:3402:200:227::2 80]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [2,932 B]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [2,932 B]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [2,008 B]
Reading package lists... Done                                      
E: The repository 'http://security.debian.org/debian-security bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://archive.ubuntu.com/ubuntu/dists/bionic/InRelease:](http://archive.ubuntu.com/ubuntu/dists/bionic/InRelease:) The key(s) in the keyring /etc/apt/trusted.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
E: The repository 'http://ftp.us.debian.org/debian bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease:](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease:) The key(s) in the keyring /etc/apt/trusted.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
E: The repository 'http://ftp.us.debian.org/debian bionic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease:](http://archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease:) The key(s) in the keyring /etc/apt/trusted.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
```

---

### Post by Dennis N on 2018-05-06
The Debian repositories with 'Err' before them aren't working. Why are they there? I suggest you disable them in the Software & Updates tool, 'Other Sources' tab. If there is some reason to have them, you need to edit the links to be correct.

---

