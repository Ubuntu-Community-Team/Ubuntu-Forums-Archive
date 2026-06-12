---
title: "Ubuntu 20 missing packages"
date: 2020-08-17
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2020-08-17
Hi,

Is the ubuntu 20 ready for upgrading? I updated ubuntu 18 to 20, there are so many problems, the package installation is worse than 18, it cannot find vim:
Package vim is not available, but is referred to by another package.

It cannot install zoom due to dependencies:

$ sudo dpkg -i ./zoom.deb
```
dpkg: dependency problems prevent configuration of zoom:
 zoom depends on libgl1-mesa-glx; however:
  Package libgl1-mesa-glx is not installed.
 zoom depends on libegl1-mesa; however:
  Package libegl1-mesa is not installed.
 zoom depends on libxcb-xtest0; however:
  Package libxcb-xtest0 is not installed.

Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu2) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for shared-mime-info (1.15-1) ...
```

$ sudo apt --fix-broken install
```

$  sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  zoom
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 159 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 131575 files and directories currently installed.)
Removing zoom (5.2.440215.0803) ...
run post uninstall script, action is remove ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for shared-mime-info (1.15-1) ...
```

When it is done, nothing installed, those dependencies are still presented, what is going with the ubuntu 20?

Thank you.

---

### Post by dino99 on 2020-08-17
Verify a few things:
- are the metapackages installed ?
- do you activated some external source(s) (like ppa) ? (which can introduce some conflicts)
- be sure to clean the system via autoclean/autoremove

---

### Post by Impavidus on 2020-08-17
> **jimhce said:**
> 
It cannot install zoom due to dependencies:

$ sudo dpkg -i ./zoom.deb
dpkg: dependency problems prevent configuration of zoom:

Better try that using```
sudo apt install ./zoom.deb
```apt can install such local .deb files and takes care of dependencies automatically.

It appears there's something wrong with your software sources. If there already was a problem on 18.04, the upgrade to 20.04 may have made it worse. Can you show us your /etc/apt/sources.list? Have you added any third-party repositories?

---

### Post by mIk3_08 on 2020-08-17
You can also try install app using GDebi Package Installer. Just add the deb file and good to go Install Package.

---

### Post by ActionParsnip on 2020-08-17
Do you mean Ubuntu 20.04 or Ubuntu 20.10 ? There is no "Ubuntu 20" it doesn't exist

---

### Post by jimhce on 2020-08-18
> **Impavidus said:**
> Better try that using```
sudo apt install ./zoom.deb
```apt can install such local .deb files and takes care of dependencies automatically.

It appears there's something wrong with your software sources. If there already was a problem on 18.04, the upgrade to 20.04 may have made it worse. Can you show us your /etc/apt/sources.list? Have you added any third-party repositories?

I should mention I did try sudo apt install ./zoom.deb, it did not work ether:

```
$ sudo apt install ./zoom.deb

Reading state information... Done
Note, selecting 'zoom' instead of './zoom.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 zoom : Depends: libgl1-mesa-glx but it is not installable
        Depends: libegl1-mesa but it is not installable
        Depends: libxcb-xtest0 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 20.04 LTS _Focal Fossa_ - Release amd64 (20200423)]/ focal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```

I did run sudo apt update.

> Verify a few things:
> - are the metapackages installed ?
> - do you activated some external source(s) (like ppa) ? (which can introduce some conflicts)
> - be sure to clean the system via autoclean/autoremove 

I never installed those in 18.04 either, but I have never got any issues to install vim and zoom, what is different in 20.04?

Also, t was not updated from 18.04, it was installed by a new 20.04 image from USB

Thanks all responses, really appreciated it

---

### Post by Impavidus on 2020-08-18
> **jimhce said:**
> I should mention I did try sudo apt install ./zoom.deb, it did not work ether:At least it gives an error message without putting package management in an inconsistent state.

The problem is that for some reason you miss a lot of repositories. You've got all the source code repositories, but not the binary repositories. Try and fix your /etc/apt/sources.list. First make a backup of your current list, then edit the list with sudoedit (which is the preferred way to edit text files for which you need root permissions).
```
cd /etc/apt
sudo cp sources.list sources.list.backup
sudoedit sources.list
```Now edit the file. Assuming you don't need the source code repositories, just replace the deb-src at the start of each line with deb, like```
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal main restricted
# becomes
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal main restricted
```You can put a # at the start of the deb-src ... partner line. If you want to keep the source code repositories, copy the lines first, so you get one with deb and one with deb-src for each repository. Then save the file and exit the text editor. If you mess up, restore your backup with```
sudo cp sources.list.backup sources.list
```
Next, run```
sudo apt update
```and all should work again.

---

### Post by jimhce on 2020-08-18
Thanks for the advice, I added deb binary to the sources.list, that got better, I was able to install vim, but still have problems to install zoom.deb:

$ sudo apt update

```
Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease               
Get:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/main i386 Packages [718 kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/main amd64 Packages [970 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/main Translation-en [506 kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/main Translation-en_AU [1,836 B]
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/main amd64 DEP-11 Metadata [494 kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/main amd64 c-n-f Metadata [29.5 kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/restricted amd64 Packages [22.0 kB]
Get:13 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/restricted i386 Packages [8,112 B]
Get:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/restricted Translation-en_AU [1,144 B]
Get:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/restricted Translation-en [6,212 B]
Get:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal/restricted amd64 c-n-f Metadata [392 B]
Fetched 2,758 kB in 5s (519 kB/s)                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
267 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

$ sudo apt install ./zoom.deb

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'zoom' instead of './zoom.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 zoom : Depends: libegl1-mesa but it is not installable
E: Unable to correct problems, you have held broken packages.
```

$ sudo apt --fix-broken install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 267 not to upgrade.
```

What I could still be missing?

Another issue is if I run ssh to that machine and to run vi to edit files, every time I pressed i key and Esc key it generated [>4, I have never seen it in ubuntu 18 and ubuntu 16, what I could be missing? It did not happen if I directly edit vi files in that machine.

Thank you very much, appreciate your kindly helps

---

### Post by jimhce on 2020-08-18
BTW, I installed libegl1-mesa-dev, but there is no libegl1-mesa

$ sudo apt install libegl1-mesa
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libegl1-mesa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libegl1-mesa' has no installation candidate
```

$ sudo apt search libegl1-mesa
```
Sorting... Done
Full Text Search... Done
libegl1-mesa-dev/focal-updates,now 20.0.8-0ubuntu1~20.04.1 amd64 [installed]
  free implementation of the EGL API -- development files
```

---

### Post by deadflowr on 2020-08-18
It look like you never enable the universe repository, 
Try
```
sudo add-apt-repository universe
sudo apt update
sudo full-upgrade
```

Then try installing zoom.

(Note I posted the full-upgrade command because you really should apply all updates first,
of course you're fine if you ignore it {it's your system} but I've found an updated system 
has fewer package installation problems, than an un-updated system)

---

### Post by Impavidus on 2020-08-19
Indeed, first install those updates.

libegl1-mesa should be available on 20.04 in the universe repo. It's actually a transitional dummy package, so there's nothing in it and it only serves to match dependencies.

Your problem with vim over ssh isn't likely to be caused by vim (as then it would happen without ssh too). I expect it to be problem with ssh or with the terminal you use on the computer you connect from.

---

### Post by jimhce on 2020-08-19
> **deadflowr said:**
> It look like you never enable the universe repository, 
Try
```
sudo add-apt-repository universe
sudo apt update
sudo full-upgrade
```

Then try installing zoom.

(Note I posted the full-upgrade command because you really should apply all updates first,
of course you're fine if you ignore it {it's your system} but I've found an updated system 
has fewer package installation problems, than an un-updated system)

Thank you very much, that did the trick to install zoom.

The only think still left is that ssh to the machine to run vi, press key i and Esc still got [>4;m[>4;2m, really annoying. Am I the only one have that problem? I've installed vim:

ii  vim            2:8.1.2269-1ubuntu5 amd64
ii  vim-common     2:8.1.2269-1ubuntu5 all
ii  vim-runtime    2:8.1.2269-1ubuntu5 all
ii  vim-tiny       2:8.1.2269-1ubuntu5 amd64

ii  openssh-client      1:8.2p1-4ubuntu0.1 amd64       
ii  openssh-server      1:8.2p1-4ubuntu0.1 amd64       
ii  openssh-sftp-server 1:8.2p1-4ubuntu0.1 amd64       

Thank you.

---

### Post by cmcanulty on 2020-08-19
also all the education metapackages are missing on 20.04. I got them from someone in ubuntued that had them on his google drive.

---

### Post by deadflowr on 2020-08-19
> **Impavidus said:**
> Indeed, first install those updates.

libegl1-mesa should be available on 20.04 in the universe repo. It's actually a transitional dummy package, so there's nothing in it and it only serves to match dependencies.

Yeah, it's definitely a weird one, since the meta-package is in universe, but the only package dependency is in main (?)
> **jimhce said:**
> Thank you very much, that did the trick to install zoom.

The only think still left is that ssh to the machine to run vi, press key i and Esc still got [>4;m[>4;2m, really annoying. Am I the only one have that problem? I've installed vim:

ii  vim            2:8.1.2269-1ubuntu5 amd64
ii  vim-common     2:8.1.2269-1ubuntu5 all
ii  vim-runtime    2:8.1.2269-1ubuntu5 all
ii  vim-tiny       2:8.1.2269-1ubuntu5 amd64

ii  openssh-client      1:8.2p1-4ubuntu0.1 amd64       
ii  openssh-server      1:8.2p1-4ubuntu0.1 amd64       
ii  openssh-sftp-server 1:8.2p1-4ubuntu0.1 amd64       

Thank you.

You should really start a different thread on that, as it's a totally different topic than what this thread is about.
(users who may know what's going on, or what you're doing wrong won't see this issue in a thread about missing packages)

---

