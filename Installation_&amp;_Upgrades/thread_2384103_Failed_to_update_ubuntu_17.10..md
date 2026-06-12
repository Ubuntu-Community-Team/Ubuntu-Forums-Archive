---
title: "Failed to update ubuntu 17.10."
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by strixtux on 2018-02-02
I am using a clean 17.10 install and I have been receiving these messages as well. Sometimes to repeat the search helps, sometimes it doesn't.

---

### Post by strixtux on 2018-02-02
What message I get running the above sudo command is:
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) artful universe
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) artful-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) artful multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) artful-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) artful-security restricted main universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates universe multiverse restricted main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports multiverse main restricted universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security multiverse

Can't find the issue, though...
Dell Inspiron 1525, 4 G RAM, 320 G HDD, Intel firmware disabled.

---

### Post by coffeecat on 2018-02-02
Posts moved to own thread.

@strixtux, please start your own thread. Even if your problem appears to be the same, there may be a different root cause, and it gets impossibly confused trying to help more than one person in one thread.

So that forum members can help, please post the terminal output of:

```
sudo apt update
```

And post it between BBCode code tags for clarity. There's a link in my sig, if you don't know how to use code tags.

---

### Post by strixtux on 2018-02-03
```

Ign:1 cdrom://Ubuntu-Studio 17.10 _Artful Aardvark_ - Release i386 (20171017.1) artful InRelease
Fehl:2 cdrom://Ubuntu-Studio 17.10 _Artful Aardvark_ - Release i386 (20171017.1) artful Release
  Bitte verwenden Sie apt-cdrom, um APT diese CD-ROM bekannt zu machen. apt-get update kann nicht dazu verwendet werden, neue CD-ROMs hinzuzufügen.
OK:3 http://archive.ubuntu.com/ubuntu artful InRelease
OK:4 http://archive.ubuntu.com/ubuntu artful-updates InRelease                 
OK:5 http://archive.ubuntu.com/ubuntu artful-backports InRelease               
OK:6 http://archive.canonical.com/ubuntu artful InRelease                      
OK:7 http://security.ubuntu.com/ubuntu artful-security InRelease            
Paketlisten werden gelesen... Fertig                
E: The repository 'cdrom://Ubuntu-Studio 17.10 _Artful Aardvark_ - Release i386 (20171017.1) artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by vasa1 on 2018-02-03
If you run```
LANG=C sudo apt update
```the output will be fully in English.

---

### Post by deadflowr on 2018-02-03
Open Software and Updates and uncheck the Installable from Cdrom/DVD option.
Then closing Software and Updates will reload the package lists  (meaning it'll run apt-get update in the background)

---

### Post by strixtux on 2018-02-03
```

Ign:1 cdrom://Ubuntu-Studio 17.10 _Artful Aardvark_ - Release i386 (20171017.1) artful InRelease
Err:2 cdrom://Ubuntu-Studio 17.10 _Artful Aardvark_ - Release i386 (20171017.1) artful Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://archive.ubuntu.com/ubuntu artful InRelease
Hit:4 http://archive.canonical.com/ubuntu artful InRelease
Get:5 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]      
Get:7 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]    
Reading package lists... Done                               
E: The repository 'cdrom://Ubuntu-Studio 17.10 _Artful Aardvark_ - Release i386 (20171017.1) artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by strixtux on 2018-02-03
Thanxalot deadflowr!
Seems the error message is gone for good.

---

