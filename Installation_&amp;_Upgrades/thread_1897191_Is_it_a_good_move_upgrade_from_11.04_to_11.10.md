---
title: "Is it a good move upgrade from 11.04 to 11.10 ?"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by amont on 2011-12-18
I upgraded from 11.04 to 11.10 shortly after its release and did all suggested updates. However, many problems remain. For example, among others:

-Synaptic crashes (just flashes at start and vanishes)
-Software-center hangs if System option is selected
-Banshee or Rhithmbox (in fact any sound app) can't find CDDB track information.

My question is: Can I expect a better performance from a fresh install of 11.10, or this kind of problems are inherent to this version and I'd do better downgrading to 11.04 (That, at least in my case, performed quite better).

---

### Post by BC59 on 2011-12-18
Can you post the contents of this file when opened?

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by amont on 2011-12-18
Thanks for your reply. Here is the contents:

```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/.Trash-1000/files/ maverick main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://es.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://es.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://es.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://es.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by BC59 on 2011-12-18
Look's ok.
Let's check the file system. Run these 2 commands and if there is a problem post it here:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by amont on 2011-12-18
No problem at all, it seems: 0 packages updated, 0 to install or to delete and 0 not updated.

---

### Post by critin on 2011-12-18
> do better downgrading to 11.04 (That, at least in my case, performed quite better).

11.10 is new, 11.04 is more stable because it's been in use longer and has had many issues worked out.

If you want to test 11.10, use it and report the bugs/errors.

It's a good idea to learn as much as you can about any new version by reading the forums and seeing the issues others are having before changing, especially if your current system is working to suit you.  Fresh installs usually work better than upgrades in any case.  

The long term 12.04 will be out in April.  It is basically 11.10 in a stable form.  For a primary os, it should be good.

---

### Post by grahammechanical on 2011-12-18
I am of the opinion, based on people reporting problems with upgrading from 11.04 to 11.10, that if anyone has anything other than a basic/default 11.04 user interface then they will have problems when upgrading. This is because there is a fundamental difference between the underlying workings of 11.04 and 11.10.

This is why I did a fresh install and I had no problems. I am also in the habit of installing each release as it comes out in its own partition. There I can test it and try to set things up the way I like. I do this before I convert my normal working Ubuntu to the new release. This way I avoid a mess.

Regards.

---

### Post by bluexrider on 2011-12-18
> **grahammechanical said:**
> I am of the opinion, based on people reporting problems with upgrading from 11.04 to 11.10, that if anyone has anything other than a basic/default 11.04 user interface then they will have problems when upgrading. This is because there is a fundamental difference between the underlying workings of 11.04 and 11.10.

This is why I did a fresh install and I had no problems. I am also in the habit of installing each release as it comes out in its own partition. There I can test it and try to set things up the way I like. I do this before I convert my normal working Ubuntu to the new release. This way I avoid a mess.

Regards.
the least amount of headaches is when fresh installs are done. I've gone the upgrade route before. the scenery wasn't pretty

---

### Post by 73ckn797 on 2011-12-18
Here is a good resource to search for previous problems posted: [http://www.googlubuntu.com/](http://www.googlubuntu.com/) I like using it over a forum search.

---

### Post by bluexrider on 2011-12-18
> **73ckn797 said:**
> Here is a good resource to search for previous problems posted: [http://www.googlubuntu.com/](http://www.googlubuntu.com/) I like using it over a forum search.
I'm going to bookmark that one now. Thanks

---

### Post by 73ckn797 on 2011-12-18
Google is your friend!:guitar:

---

### Post by JustinR on 2011-12-18
In my opinion no. I've never had so many issues with Ubuntu before, although the underlying reason is probably Gnome3. While I don't have any issues with the Unity/Gnome3 changes, this is just unacceptable.

Whether you do an upgrade or fresh install, (I did a fresh install), you might have problems. Gnome3 constantly freezes on me, especially when opening Unity Dash. Suspend/Resume takes much longer than normal.


Also a general note, no matter if you have issues or not with upgrading/fresh install, Gnome 3 is definitely under-featured, e.g. many many many features are missing from Gnome 2. Because Gnome3 is a new project, it's to be expected but I was astounded at the lack of usability in Gnome3.\

/end-rant, although though the Unity changes in Ubuntu 11.10 do look nice, so it may be worth it.

---

### Post by 73ckn797 on 2011-12-18
> **JustinR said:**
> In my opinion no. I've never had so many issues with Ubuntu before, although the underlying reason is probably Gnome3. While I don't have any issues with the Unity/Gnome3 changes, this is just unacceptable.

Whether you do an upgrade or fresh install, (I did a fresh install), you might have problems. Gnome3 constantly freezes on me, especially when opening Unity Dash. Suspend/Resume takes much longer than normal.


Also a general note, no matter if you have issues or not with upgrading/fresh install, Gnome 3 is definitely under-featured, e.g. many many many features are missing from Gnome 2. Because Gnome3 is a new project, it's to be expected but I was astounded at the lack of usability in Gnome3.\

/end-rant, although though the Unity changes in Ubuntu 11.10 do look nice, so it may be worth it.

Fresh installs are best IMO. 

Off Topic: Gnome 3 is just about as feature filled as Gnome 2. There are tweaks to get it working close to Gnome 2. Things are different but I am already adjusted to those changes. I uninstalled Unity completely.

---

### Post by critin on 2011-12-18
> **73ckn797 said:**
> Here is a good resource to search for previous problems posted: [http://www.googlubuntu.com/](http://www.googlubuntu.com/) I like using it over a forum search.

I think the forums are better in this case because if you don't have a specific problem yet, (before installing) you won't know what to search for.  Reading the forums and the answers give an indication of what might apply to the user, and how easy it will be, or not, to fix.  Besides its a great learning tool that all new users should take advantage of.  For specific problems, the link is great--I'm going to bookmark it.  Thanks!

---

### Post by 73ckn797 on 2011-12-18
> **critin said:**
> I think the forums are better in this case because if you don't have a specific problem yet, (before installing) you won't know what to search for.  Reading the forums and the answers give an indication of what might apply to the user, and how easy it will be, or not, to fix.  Besides its a great learning tool that all new users should take advantage of.  For specific problems, the link is great--I'm going to bookmark it.  Thanks!
The Googlubuntu search allows phrase searches, something that I have found to be difficult on the forum search. I have yet to figure that out.
Just a matter of preference, however.

---

### Post by bluexrider on 2011-12-18
> **73ckn797 said:**
> Fresh installs are best IMO. 

Off Topic: Gnome 3 is just about as feature filled as Gnome 2. There are tweaks to get it working close to Gnome 2. Things are different but I am already adjusted to those changes. I uninstalled Unity completely.
so in all honesty what does Gnome 3 have over Gnome 2 besides the kernel

---

### Post by critin on 2011-12-18
> something that I have found to be difficult on the forum search.

So have I!  lol   It's almost impossible to find a specific problem through search, and so your link will be useful to me.  I didn't know of it.  I guess I'm talking about new users who haven't used linux much and need to research in general.

---

### Post by 73ckn797 on 2011-12-18
> **bluexrider said:**
> so in all honesty what does Gnome 3 have over Gnome 2 besides the kernel
No advantage but different. I can still use Ubuntu as I have for 5 years. I use it 99.99% of my computing requirements. I am at the age where I either can become crotchety or accept that things change. Either I make adjustments or become more set in my ways. The latter is not a good way to live though some things are non-negotiable, computing is not one of those areas.

---

### Post by bluexrider on 2011-12-19
> **73ckn797 said:**
> No advantage but different. I can still use Ubuntu as I have for 5 years. I use it 99.99% of my computing requirements. I am at the age where I either can become crotchety or accept that things change. Either I make adjustments or become more set in my ways. The latter is not a good way to live though some things are non-negotiable, computing is not one of those areas.
It just further deepens my feelings toward Gnome 3. It doesn't have anything I want right now.

---

### Post by amont on 2011-12-19
Thank you very much for all your sensible responses. As a user with little experience, it seems that I rushed a little in upgrading the version. I succumbed to the pop-up messages inviting me to do so. :(

---

### Post by bluexrider on 2011-12-20
> **amont said:**
> Thank you very much for all your sensible responses. As a user with little experience, it seems that I rushed a little in upgrading the version. I succumbed to the pop-up messages inviting me to do so. :(
Personally I don't think they should be there.

---

