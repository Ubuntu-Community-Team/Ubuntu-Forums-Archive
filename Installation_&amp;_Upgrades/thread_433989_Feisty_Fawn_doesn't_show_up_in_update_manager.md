---
title: "Feisty Fawn doesn't show up in update manager"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Deadpool14 on 2007-05-05
Hi, 
I'm using Edgy Eft but when I try to upgrade to feisty fawn it never shows up in my update manager.  Is there something special I have to do to make this work?
(I'm following instructions from here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading))
Thanks in advance

---

### Post by jfinkels on 2007-05-05
> **Deadpool14 said:**
> Hi, 
I'm using Edgy Eft but when I try to upgrade to feisty fawn it never shows up in my update manager.  Is there something special I have to do to make this work?
(I'm following instructions from here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading))
Thanks in advance

Try typing the following command in the terminal:
```

gksudo "update-manager -c"

```

---

### Post by Deadpool14 on 2007-05-05
No such luck however when I typed into the terminal window i did get this before software updates came up:
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files)

---

### Post by jfinkels on 2007-05-05
> **Deadpool14 said:**
> No such luck however when I typed into the terminal window i did get this before software updates came up:
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files)

Excellent. Can you post the output of the following command:
```
cat /etc/apt/sources.list
```

---

### Post by Deadpool14 on 2007-05-05
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by jfinkels on 2007-05-05
Looks like your sources.list is fine. To be honest, I don't know what that error message means, but it certainly isn't normal. Perhaps it's a problem on the server side?

---

