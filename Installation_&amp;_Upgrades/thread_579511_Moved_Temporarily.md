---
title: "Moved Temporarily?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by geeree on 2007-10-18
Hi,

I am using Ubuntu 7.04 on a Dell Inspiron 640m and trying to upgrade to Ubuntu 7.10 using the Update Manager. I get the following error: 

> Could not download all repository indexes

The repository might be no longer available or could not be contacted
because of network problems. If available an older version of the failed
index will be used. Otherwise the repository will be ignored. Check your
network connection and the correct writing of the repository address in
the preferences.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Moved Temporarily
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Moved Temporarily


My network connection is fine. This has been happening for more than 30 minutes now. Could anybody explain what this means? Are there any alternate means for me to upgrade to Gutsy Gibbon? 

Thanks.

Girish.

---

### Post by PmDematagoda on 2007-10-18
Please disable the medibuntu repositories by putting the # in front of them, use this:-

```
sudo gedit /etc/apt/sources.list
```

to edit the sources.list file.

---

### Post by geeree on 2007-10-18
> **PmDematagoda said:**
> Please disable the medibuntu repositories by putting the # in front of them &hellip;


That takes care of the error message but I still don't see Gutsy Gibbon! Has anyone here tried upgrading in this (I suppose, officially recommended) way? 

Girish.

---

### Post by PmDematagoda on 2007-10-18
I suggest you have a look at this:-

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by geeree on 2007-10-18
> **PmDematagoda said:**
> I suggest you have a look at this:-

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Thanks, but that is *exactly* what I am following. According to the step 2, I click on the `Check' button in the Update Manager. And then it just says "Your system is up-to-date." The message "New distribution release '7.10' is available" never comes up! 

Girish.

---

### Post by PmDematagoda on 2007-10-18
Could you please post your sources.list file?

---

### Post by geeree on 2007-10-18
> **PmDematagoda said:**
> Could you please post your sources.list file?

Sure. Here it is: 
```

deb http://ubuntu.beryl-project.org feisty main

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty multiverse
#AUTOMATIX REPOS END

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
  deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
## deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free


```

One medibuntu line is not commented out here. But I tried working with that too. Didn't help. 

Thanks. 

Girish.

---

### Post by silkstone on 2007-10-18
geeree - I've just been through exactly the same procedure as you describe, got the same message about the medibuntu repos, and now the 'Update to Gutsy' message is missing from Update Manager for me too.

I know that doesn't help, but I thought you'd like to know that you're not alone!

---

### Post by silkstone on 2007-10-18
Ah - If I click on the Check button the invitation reappears,

---

### Post by geeree on 2007-10-18
> **silkstone said:**
> geeree - I've just been through exactly the same procedure as you describe, got the same message about the medibuntu repos, and now the 'Update to Gutsy' message is missing from Update Manager for me too.

I know that doesn't help, but I thought you'd like to know that you're not alone!

Thanks, silkstone. Yeah, that's a relief! And does that mean we are supposed to wait for some time before the upgrade is really available? 

Girish.

---

### Post by geeree on 2007-10-18
> **silkstone said:**
> Ah - If I click on the Check button the invitation reappears,

Does that mean I am alone again? What happened to your medibuntu message?

Girish.

---

### Post by geeree on 2007-10-20
Okay, it got sorted out. The upgrade is complete and I am writing this from Gutsy! I had to comment out the medibuntu lines in sources.list but I don't why that didn't work on Thursday! Thanks, PmDematagoda and silkstone. 

Girish.

---

### Post by Slave5Tom on 2007-10-20
Hi geeree:
I had the exact same problem with the medibuntu repositories.  Unfortunately sudo gedit /etc/apt/sources.list didn't change the error, even when I commented the medibuntu lines out.  However, I did find a way to remove these by using the Ubuntu menu >System>Administration>Software Sources.  Pick Third-Party Software tab then un-select the medibuntu repositories.  I'm still not sure why the terminal edit did not work, but the menu method seem to work so far.  (I'm in the middle of an update right now - no crap-out yet)

---

### Post by geeree on 2007-10-20
> **Slave5Tom said:**
> 
I had the exact same problem with the medibuntu repositories.  Unfortunately sudo gedit /etc/apt/sources.list didn't change the error, even when I commented the medibuntu lines out.  However, I did find a way to remove these by using the Ubuntu menu >System>Administration>Software Sources.  Pick Third-Party Software tab then un-select the medibuntu repositories.  I'm still not sure why the terminal edit did not work, but the menu method seem to work so far.  (I'm in the middle of an update right now - no crap-out yet)

Yes Slave5Tom, this shouldn't have happened really. I'm afraid I don't know a reason too. There's another thread around here where they're taking a poll of how your upgrade/install was and I suggested that the upgrade procedure should be more transparent. For example, I don't even understand why third-party repositories are such a problem while upgrading. 

Hope your upgrade remains trouble-free! 

Girish.

---

### Post by gibrovacco on 2007-10-30
Hello,

I got the same problem upgrading an xubuntu feisty to gutsy... I think this maybe caused from an uncompleted upgrade (i.e. caused from the (in)famous "302 moved" error for some packages).. The result is an hybrid system with some packages from feisty and the upgrade manager being sure it is gutsy... All I made was subsituting, in sources.list, "feisty" with "gutsy", and the update manager was able to understand there was an incomplete upgrade.

I hope this may save someone from an headache :)

---

