---
title: "Update wont let me update."
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by wcrwmm on 2018-05-01
I keep getting this error message when trying to run the update manager. I am trying to upgrade to 18.04 from 17.10

  E:The repository 'http://security.ubuntu.com/ubuntu yakkety-security Release' no longer has a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://us.archive.ubuntu.com/ubuntu yakkety-updates Release' no longer has a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://us.archive.ubuntu.com/ubuntu yakkety-backports Release' does not have a Release file.

I can not get the new distro to appear so I can upgrade.  running 17.10 on a Levento AMD E1-6010 APU with AMD Radeon R2 Graphics × 2 .  How do I see this apt-secure(8) manpage?

Yakkety was 16.10?  Why am I trying to get information for a release that was updated a year ago?  I am running 17.10 now.  Why is it not showing the repository for that release?

---

### Post by logix2 on 2018-05-01
Yakkety (16.10) is not a long term release and therefore is only supported for 9 months. It's end of life was reached a while back, so you should upgrade / install the latest Ubuntu 18.04 LTS, which was released a few days ago and is supported for 5 years. See here for a list of Ubuntu releases (scroll for the End Of Life list): [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Impavidus on 2018-05-01
It seems that, for whatever reason, some 16.10 repositories were left in your sources.list.

Let's see the complete output of```
sudo apt update
```
Also show the contents of /etc/apt/sources.list:```
cat /etc/apt/sources.list
```Maybe you just have to comment out a few lines.

---

### Post by wcrwmm on 2018-05-02
That is exactly what I am trying to do..... and I know 16.10 is no longer supported.  I am running 17.10.  That is the problem.

```
Ign:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates InRelease         
Ign:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports InRelease       
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates Release
  404  Not Found [IP: 91.189.91.26 80]
Ign:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security InRelease
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports Release
  404  Not Found [IP: 91.189.91.26 80]
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security Release
  404  Not Found [IP: 91.189.88.161 80]
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful InRelease
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates InRelease
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports InRelease
Hit:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security InRelease
Hit:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-proposed InRelease
Hit:12 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease
Hit:13 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety InRelease
Reading package lists... Done                       
E: The repository 'http://us.archive.ubuntu.com/ubuntu yakkety-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu yakkety-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu yakkety-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

List is
```
# deb cdrom:[Ubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.2)]/ yakkety main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful multiverse universe main restricted #Added by software-properties
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates multiverse universe main restricted #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports main restricted universe multiverse #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security multiverse universe main restricted #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful main
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security multiverse
```



 and

---

### Post by PaulW2U on 2018-05-02
> **wcrwmm said:**
> That is exactly what I am trying to do..... and I know 16.10 is no longer supported.  I am running 17.10.  That is the problem.
In a terminal - type the following command
```
sudo nano /etc/apt/sources.list
```
Comment out by adding a '#' to the start of each line that refers to yakkety.
Save the file with Ctrl-O and Ctrl-X

Then:
```
sudo apt update
sudo apt upgrade

```
What do you now see?

---

### Post by wcrwmm on 2018-05-02
I may end up doing a fresh install it may be a lot easier than messing with all this.   Now beginning to remember why I went back to Windows last time.

---

### Post by PaulW2U on 2018-05-02
> **wcrwmm said:**
> I may end up doing a fresh install it may be a lot easier than messing with all this.   Now beginning to remember why I went back to Windows last time.Please do try what I have suggested. :)

If you are running Artful then your sources.list file should **only** have references to that release.

---

### Post by wcrwmm on 2018-05-02
```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful InRelease
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates InRelease [88.7 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports InRelease [74.6 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security InRelease [83.2 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-proposed InRelease [240 kB]
```

```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful InRelease
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates InRelease [88.7 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports InRelease [74.6 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security InRelease [83.2 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-proposed InRelease [240 kB]
Fetched 486 kB in 2s (187 kB/s)                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

seem to be working now, thank you.

---

