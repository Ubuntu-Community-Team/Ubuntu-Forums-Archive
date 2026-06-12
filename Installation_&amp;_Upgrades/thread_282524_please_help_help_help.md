---
title: "please help help help"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by abu3abdalla on 2006-10-22
i am trying to install xgl and the eroor is 
libwnck18:
  Depends: libatk1.0-0 (>=1.12.1) but 1.11.4-0ubuntu1 is to be installed
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed
  Depends: libcairo2 (>=1.2.4) but 1.0.4-0ubuntu1 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.10.3) but 2.8.20-0ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.14.5) but 1.12.3-0ubuntu3 is to be installed

so how can i solve this error??????????????????????????

---

### Post by Qrk on 2006-10-22
You should post the file /etc/apt/sources.list here. It looks like you may be using sources that conflict.

---

### Post by abu3abdalla on 2006-10-23
thank u very much but still i do not know what can i do? so please tell me

---

### Post by wpshooter on 2006-10-23
Please use your text editor program (It is found on one of your drop down menus - I can not remember exactly which one it is on - I am at work right now) to open the sources.list file at the location shown in the above post and then copy and paste or attach it to a post so that QRK can take a look at it.

---

### Post by Kateikyoushi on 2006-10-23
Copy this to the terminal.
```
gedit /etc/apt/sources.list
```

When it is opened in the editor post the content of the file to the forum.

---

### Post by abu3abdalla on 2006-10-23
thank u all and this is the list:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy


deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


so please tell me the problem:-k

---

### Post by bulldog on 2006-10-23
You shouldn't mix dapper and edgy repositories.

Remove the Edgy repo!!

---

