---
title: "Yahoo problem"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by luckyking8 on 2010-04-04
Hello Brother I m not able to instal the Yahoo........ they msg show Error: Dependency is not satisfiable: libgdk-pixbuf2 (>= 0.13.0)
.. i install all the files but  :sad: :sad: :sad: :sad: plz some one help me


Regarding 

Lucky

---

### Post by loell on 2010-04-04
hi, use empathy or pidgin for yahoo instant messaging,

kopete or gyachi if you like webcam support.

---

### Post by luckyking8 on 2010-04-04
i m not able to instal 
**Pidgin**


i m new user of ubuntu plz tell me:(((

---

### Post by lisati on 2010-04-04
> **luckyking8 said:**
> i m not able to instal 
**Pidgin**


i m new user of ubuntu plz tell me:(((

Are you getting an error message?

---

### Post by luckyking8 on 2010-04-04
i dont know how to instal:(

---

### Post by lisati on 2010-04-04
> **luckyking8 said:**
> i dont know how to instal:(

Have a look on your Applications->Internet menu, pidgin might already be installed. 

An easy way to install stuff on 9.04 or earlier is with the Applications->Add/Remove Software menu item. With 9.10, look for Applications->Software Center.

---

### Post by Sef on 2010-04-04
> Have a look on your Applications->Internet menu, pidgin might already be installed. 

That would be true in you are using 9.04 or earlier.  Pidgin was installed by default.

> An easy way to install stuff on 9.04 or earlier is with the Applications->Add/Remove Software menu item. With 9.10, look for Applications->Software Center.

Also if installing pidgin in 9.10 or later version, Edit > Software Sources > tic Community Maintained Software Sources (Universe.)

---

### Post by luckyking8 on 2010-04-04
no softwear instal there:(

---

### Post by lisati on 2010-04-04
> **Sef said:**
> 
Also if installing pidgin in 9.10 or later version, Edit > Software Sources > tic Community Maintained Software Sources (Universe.)

Thanks for the update (I'm still using 9.04)

---

### Post by luckyking8 on 2010-04-04
i am using 9.10

---

### Post by Sef on 2010-04-04
> no softwear instal there:sad:Sounds like a problem with your sources list possibly, but something is not right.

Applications > Accessories > Terminal

then copy and paste in this command

```
cat /etc/apt/sources.list
```

then copy and paste the results here.


> Thanks for the update (I'm still using 9.04)     welcome.

---

### Post by luckyking8 on 2010-04-04
lucky@lucky-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) karmic main
lucky@lucky-desktop:~$

---

### Post by luckyking8 on 2010-04-04
Plz do some thing for me tell me how i can instal the file :((

---

### Post by lisati on 2010-04-04
Have you tried the Software Center on your Applications menu yet?

---

### Post by luckyking8 on 2010-04-04
there is no any softwer instal there:(



can u come in my pc through Remote.... if yes then plz tell me the seting i ll shair my pc

---

### Post by lisati on 2010-04-04
> **luckyking8 said:**
> there is no any softwer instal there:(



can u come in my pc through Remote.... if yes then plz tell me the seting i ll shair my pc

I use an older version of Ubuntu which uses a different option on the menu.

---

