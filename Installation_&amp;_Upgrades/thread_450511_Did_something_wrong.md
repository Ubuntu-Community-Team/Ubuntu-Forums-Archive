---
title: "Did something wrong"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by RDUBBALO on 2007-05-21
Ok I was trying to upgrade to 7.04 and it said there was and error it couldnt get some files. so I went into gedit to remove them they were wine files. anyway now I cannot open update manager. now i have a new eroor. 
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
any ideas on what I need to do here. i have to put that line back in and then i need to figure out what to do to upgrade properly. Thanks

---

### Post by taurus on 2007-05-21
There is something wrong with line 57 in /etc/apt/sources.list.  So, you either need to fix it yourself or post it here.

```
cat /etc/apt/sources.list
```

---

### Post by RDUBBALO on 2007-05-21
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

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

---

### Post by taurus on 2007-05-21
Are you sure that is the complete list of /etc/apt/sources.list?  I count only 53 lines in there.

---

### Post by RDUBBALO on 2007-05-22
> **taurus said:**
> Are you sure that is the complete list of /etc/apt/sources.list?  I count only 53 lines in there.

yeah I think I deleted those lines thats the problem they were something to do with wine

---

### Post by RDUBBALO on 2007-05-22
cat /etc/apt/sources.list

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

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe


 sudo apt-key add -

---

### Post by RDUBBALO on 2007-05-22
What if I just download 7.04 and brun the iso file to a disk when i run it in the computer can i just upgrade and it will fix those lines?

---

### Post by taurus on 2007-05-22
What's the error message when you run this command from a terminal now?

```
sudo aptitude update
```

---

### Post by RDUBBALO on 2007-05-22
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by taurus on 2007-05-22
Can you please post the complete /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by RDUBBALO on 2007-05-23
:~$ cat /etc/apt/sources.list

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

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe


 sudo apt-key add -

---

### Post by taurus on 2007-05-23
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the last line from your list.

```
sudo apt-key add -
```
Save it and then update your list again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by RDUBBALO on 2007-05-23
(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17886): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Error: no "edit" mailcap rules found for type "application/*"

---

### Post by RDUBBALO on 2007-05-26
any luck with this problem

---

### Post by RDUBBALO on 2007-05-27
Tarus where did you go. I don't know if you found out what I did wrong here I think i deleted some line that i really needed.

---

### Post by taurus on 2007-05-27
Did you remove that last line in your /etc/apt/sources.list?

```
sudo apt-key add -
```

You can edit it with

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by RDUBBALO on 2007-05-28
Thanks brother you are the best.

---

