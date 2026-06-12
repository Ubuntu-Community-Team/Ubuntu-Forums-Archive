---
title: "Problem in software installation"
date: 2017-05-12
forum: Installation &amp; Upgrades
---

### Post by lcerrotti on 2017-05-12
Hi all, I  present with a problem in installing anything, recently download linux  and I do not understand too much about the subject and I wanted to know  if you can give me a hand in this:
When proceeding with the installation of the package the following error appears in the terminal:

EXAMPLE WITH GOOGLE CHROME: (THE PACKAGE IS ALREADY DOWNLOADED)

1) INSTALATION CODE:

lautaro@lautaro-MAX-G0101:~$ ```
sudo  apt install gconf-service gconf-service-backend gconf2-common  libappindicator1 libgconf-2-4 libindicator7 libpango1.0-0  libpangox-1.0-0
[sudo] password for lautaro:



2) ERROR:

E: Line 1 malformed in the list of sources /etc/apt/sources.list (type)
E: Could not read source lists.
E: Line 1 malformed in the list of sources /etc/apt/sources.list (type)
E: Could not read source lists.




 #(SOURCE LIST)




 mie#deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted

 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty multiverse universe restricted main

 ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-updates multiverse universe restricted main

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty universe
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-updates universe
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-updates universe

 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-updates multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-updates multiverse

 ## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse

 ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse universe restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
```


I would appreciate your help, regards Lautaro Cerrotti

PS: This happens with any kind of installation, besides I can not install the package in any other way

---

### Post by wildmanne39 on 2017-05-12
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please do not use all capital letters in a word or sentence it is considered rude, and this is an English only forum so please translate the error messages so someone can help you.

Thanks

---

### Post by deadflowr on 2017-05-12
This is line 1
```
mie#deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted
```
is this right? it shows mie#
If so, remove the mie from the line
and save the file.
Then run
```
sudo apt update
```
the try installing packages.

---

