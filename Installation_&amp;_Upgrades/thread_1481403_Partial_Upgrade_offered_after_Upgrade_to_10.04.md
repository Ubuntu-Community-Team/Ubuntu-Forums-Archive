---
title: "Partial Upgrade offered after Upgrade to 10.04"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by theneoindian on 2010-05-12
Hi , 

I upgraded my Karmic to Lucid 10.04 using alternate cd . Now after that , when i run the Update manager , it offers a Partial Upgrade and when i accept that , it goes on and try to UPGRADE the system AGAIN to 10.04 . What can i do to fix it ? 

[CENTER][IMG]https://files.one.ubuntu.com/b8CRFONTTXSOsS9G6s131Q[/IMG][/CENTER]

I've been trying for days in hope of fixing this since i thought it might be due to some inconsistencies in the repositories , but no change . so there's something wrong wid my system i guess ...

---

### Post by jjcv on 2010-05-13
Very hard to answer your question without lots more detail.   Have you tried doing a:

sudo aptitude update
sudo aptitude safe-upgrade

and see how that goes.

---

### Post by theneoindian on 2010-05-13
> **jjcv said:**
> Very hard to answer your question without lots more detail.   Have you tried doing a:

sudo aptitude update
sudo aptitude safe-upgrade

and see how that goes.

Hi ,  i did it . This is the output of sudo aptitude safe-upgrade :

```

Resolving dependencies...
The following packages have been kept back:
  akregator kaddressbook kalarm kbugbuster kdeadmin kdebase-workspace kdebase-workspace-bin 
......................
The following packages will be REMOVED:
  awn-manager{u} deluge-core{u} kde-icons-oxygen{u} kdebase-runtime-bin-kde4{u} 

.........................................

The following packages are RECOMMENDED but will NOT be installed:
  dolphin libavcodec-extra-52 valgrind winbind 
462 packages upgraded, 114 newly installed, 39 to remove and 23 not upgraded.
Need to get 873MB/877MB of archives. After unpacking 229MB will be used.


```

The output has been edited to reduce it . It says it need to install 873 mb . Please help me understand what is happening ...

This is somewhat similar to what i get when i run the Update Manager : 

[CENTER][IMG]http://img269.imageshack.us/img269/2200/27607284.png[/IMG][/CENTER]

Please explain what is goin on ...

---

### Post by quequotion on 2010-05-13
If you upgraded from CD, and chose not to check for updates online, then your upgrade is not finished.

Ubuntu was upgraded, but since the CD was published many packages have been updated. You should agree to update those packages.

Also, be sure that your CD is the final release and not one of the Release Candidates. There was a little confusion on Ubuntu's home page on the release date.




# also +1 for a thread happening in the eastern hemisphere

---

### Post by theneoindian on 2010-05-13
> **quequotion said:**
> If you upgraded from CD, and chose not to check for updates online, then your upgrade is not finished.

Ubuntu was upgraded, but since the CD was published many packages have been updated. You should agree to update those packages.

Also, be sure that your CD is the final release and not one of the Release Candidates. There was a little confusion on Ubuntu's home page on the release date.




# also +1 for a thread happening in the eastern hemisphere
So , u are saying that the upgrade is for the packages only and not for the distro ,rite ? I thought it was for the entire distro upgrade since the packages were >800MB . 
So , is it safe to go ahead with the partial upgrade ?

Hey ,I suppose i can remove some of the unused applications like KDE and thus reduce the upgrade size . am i rite in this ?

So with this assumption , I tried removing  some kde apps , but the package manager says that it is going to remove allmost all the kde applications .. Please comment on this . It's like i select cervisia to be removed and the package manager is gonna remove many other unrelated kde apps like ktorrent along with it . 

So how can i go about removing only the kde apps i don't need ? In fact I don' use KDE and wanna remove the DE , but still like to keep aps like ktorrent . These some apps only need the qt libraries i guess .. correct me if i'm wrong

---

### Post by dino99 on 2010-05-13
why are you not ugrading your sources.list to 10.04 with only the genuine lucid repo, then update, upgrade ?

you can add your cd to sources.list too then update upgrade if you have problem to upgrade using the network

---

### Post by theneoindian on 2010-05-13
> **dino99 said:**
> why are you not ugrading your sources.list to 10.04 with only the genuine lucid repo, then update, upgrade ?

you can add your cd to sources.list too then update upgrade if you have problem to upgrade using the network
Please expand on upgrading sources.lst to 10.04 . What do you mean by valid lucid repo ? The upgrade from karmic to lucid disabled my third party repos and i'vent changed that . The current repos are the main and multiverse lucid repos . There are no repos dat i can remove .. Please reply ..

---

### Post by quequotion on 2010-05-13
> **theneoindian said:**
> So , u are saying that the upgrade is for the packages only and not for the distro ,rite ? I thought it was for the entire distro upgrade since the packages were >800MB . 
So , is it safe to go ahead with the partial upgrade ?

Hey ,I suppose i can remove some of the unused applications like KDE and thus reduce the upgrade size . am i rite in this ?

So with this assumption , I tried removing  some kde apps , but the package manager says that it is going to remove allmost all the kde applications .. Please comment on this . It's like i select cervisia to be removed and the package manager is gonna remove many other unrelated kde apps like ktorrent along with it . 

So how can i go about removing only the kde apps i don't need ? In fact I don' use KDE and wanna remove the DE , but still like to keep aps like ktorrent . These some apps only need the qt libraries i guess .. correct me if i'm wrong


It is very possible that the post-upgrade updates are greater than 800MB.

I'm doing an online upgrade at the moment, which will download 1,600MB of packages from the latest updates. Even in a few days, especially just after a major release, a lot of unknown bugs can appear and fixes will be made.

As for KDE packages, I really don't know what to say. Why do you have so many KDE packages? Did you upgrade from kubuntu or xubuntu? Did you install them yourself?

You might want to give "aptitude" a try. It does a better job of explaining why it wants to remove other apps```
sudo aptitude remove package
```"package" is the app you don't want.

---

### Post by quequotion on 2010-05-13
> **theneoindian said:**
> Please expand on upgrading sources.lst to 10.04 . What do you mean by valid lucid repo ? The upgrade from karmic to lucid disabled my third party repos and i'vent changed that . The current repos are the main and multiverse lucid repos . There are no repos dat i can remove .. Please reply ..

Could you post your sources.list file for us? Just in case!

Sounds like you have some idea of what he meant. In /etc/apt/sources.list you should see several lines like:```
deb http://repo.url.here lucid main # Example Lucid Repo with a "main" branch
``` If any of those lines read```
deb http://repo.url.here karmic main # Example Karmic Repo with a "main" branch
```then you could have some trouble.

---

### Post by quequotion on 2010-05-13
> **dino99 said:**
> why are you not ugrading your sources.list to 10.04 with only the genuine lucid repo, then update, upgrade ?

you can add your cd to sources.list too then update upgrade if you have problem to upgrade using the network

I think he's past that step.

---

### Post by theneoindian on 2010-05-13
This is my sources.list file :

```
# added by the release upgrader
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.oss.eznetsols.org/ubuntu/ lucid main restricted
deb-src http://ubuntu.oss.eznetsols.org/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.oss.eznetsols.org/ubuntu/ lucid universe
deb-src http://ubuntu.oss.eznetsols.org/ubuntu/ lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.oss.eznetsols.org/ubuntu/ lucid multiverse
deb-src http://ubuntu.oss.eznetsols.org/ubuntu/ lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

# deb http://dl.google.com/linux/deb/ stable non-free main # disabled on upgrade to lucid
# deb http://dl.google.com/linux/deb/ testing non-free # disabled on upgrade to lucid

```

As u may note , it doesn't contain any karmic repos . 
Can someone tell me why package manager removes completely unrelated packages when i tell it to remove some package ? Is it because it is stupid ? is there any other way to safely remove packages other than via apt-get or package manager ? too many questions eh ?? :)

---

### Post by quequotion on 2010-06-11
> **theneoindian said:**
> 
Can someone tell me why package manager removes completely unrelated packages when i tell it to remove some package ? Is it because it is stupid ? is there any other way to safely remove packages other than via apt-get or package manager ? too many questions eh ?? :)

It is stupid, very stupid. Brain dead in fact. You have to tell it exactly how to do everything or these kind of "accidents" happen.

I found a trick that might help in the future (can't do anything for the lost packages) in **/etc/apt.conf** add:```
APT::Clean-Installed=false
```That should reduce the list of packages that get deleted when doing an ```
apt-get dist-upgrade
```This will keep outdated/unsupported packages you have chosen to install (often they are simply temporarily not available from the usual repository and come back later)

I am not so impressed with the upgrade manager in Ubuntu however. It takes me about two weeks to get my computer back to usual after an upgrade.  Recently however, I found a method that reduced my post-upgrade woes. If you're still having trouble, search the forum for my thread on "Debian upgrade method" which no one has replied to...

---

### Post by theneoindian on 2010-06-12
> **quequotion said:**
> It is stupid, very stupid. Brain dead in fact. You have to tell it exactly how to do everything or these kind of "accidents" happen.

I found a trick that might help in the future (can't do anything for the lost packages) in **/etc/apt.conf** add:```
APT::Clean-Installed=false
```That should reduce the list of packages that get deleted when doing an ```
apt-get dist-upgrade
```This will keep outdated/unsupported packages you have chosen to install (often they are simply temporarily not available from the usual repository and come back later)

I am not so impressed with the upgrade manager in Ubuntu however. It takes me about two weeks to get my computer back to usual after an upgrade.  Recently however, I found a method that reduced my post-upgrade woes. If you're still having trouble, search the forum for my thread on "Debian upgrade method" which no one has replied to...

I will try that .. But there's no file /etc/apt.conf

---

### Post by quequotion on 2010-06-12
> **theneoindian said:**
> I will try that .. But there's no file /etc/apt.conf

indeed, forgot to mention it won't exist until you make it.

alternatively you could put this option in one of the files in /etc/apt/apt.conf.d/ which is the "modern" way of doing things, but I tend to forget which file and what changes I made unless I keep them strictly separated.

---

