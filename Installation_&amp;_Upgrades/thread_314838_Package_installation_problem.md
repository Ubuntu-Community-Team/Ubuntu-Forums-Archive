---
title: "Package installation problem"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by vivin_west on 2006-12-08
vivin@vivin-desktop:~$ gksudo gedit etc/apt/sources.list

(gksudo:18345): Gdk-WARNING **: locale not supported by Xlib

(gksudo:18345): Gdk-WARNING **: cannot set locale modifiers

** (gksudo:18345): WARNING **: Owner of /tmp/orbit-vivinzdauser is not the current user

(gedit:18346): Gdk-WARNING **: locale not supported by Xlib

(gedit:18346): Gdk-WARNING **: cannot set locale modifiers

(gedit:18346): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
vivin@vivin-desktop:~$ sudo gedit etc/apt/sources.list
Password:

(gedit:18832): Gdk-WARNING **: locale not supported by Xlib

(gedit:18832): Gdk-WARNING **: cannot set locale modifiers
vivin@vivin-desktop:~$

Can anyone help me fix this error. I am unable to instal any pacakages. Further I am getting errors in the repositories window.

---

### Post by vivin_west on 2006-12-08
I am unable to open and modify sources.list

---

### Post by taurus on 2006-12-08
```
sudo nano -Bw  /etc/apt/sources.list
```

---

### Post by vivin_west on 2006-12-10
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb [http://download.skype.com/linux/repos/debian/stable](http://download.skype.com/linux/repos/debian/stable) non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)



                                    [ line 1/34 (2%), col 1/1 (100%), char 0/1546 (0%) ]
^G Get Help         ^O WriteOut         ^R Read File        ^Y Prev Page        ^K Cut Text         ^C Cur Pos
^X Exit             ^J Justify          ^W Where Is         ^V Next Page        ^U UnCut Txt        ^T To Spell


what next??

---

### Post by vivin_west on 2006-12-10
I also got a message saying malformed line no 31 when I opened Synaptic. In the Synaptic window no package list exist.

---

### Post by anubhavrocks on 2006-12-11
try doing 


anubhav@anubhav-desktop:~$ gksu gedit /etc/apt/sources.list

after you open the file in gedit 

comment the line number 31 by prefixing the line with #,save the file.

Now try running synaptic

---

### Post by vivin_west on 2006-12-11
Thanks dude.
I fixed that line in the same window.All is fine now

---

