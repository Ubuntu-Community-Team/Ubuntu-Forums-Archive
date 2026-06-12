---
title: "Can't access Universe repository"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by m_vrik on 2007-02-24
I'm having trouble accessing the Universe repository to install Wine.  I keep timing out when it trys to access the archive.Ubuntu.org.  Below is my "sources.list" file.


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Why am I having this difficulty?  Thanks

---

### Post by bapoumba on 2007-02-24
Hello,
I've read here and there that the us repos were having some difficulties. Try to remove the "us" part of the repos in /etc/apt/sources.list.
Open a terminal (> Accessories > Terminal) and run:
```
sudo nano -B /etc/apt/sources.list
```
CTRL-O to save with the same name, CTRL-X to exit.

then run:
```
sudo aptitude update
```

---

### Post by rudiz on 2007-02-24
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

complete the second line with main restricted multiverse

---

### Post by m_vrik on 2007-02-24
Sorry for the delayed response - I had to clear the driveway of snow.  "rudiz", I made the changes in the second line that you suggested but I still had the same problem connecting.
"bapoumba", I did what you suggested also, but to no avail; still timed out.  Thanks for your suggestions, but problem is still unresolved.

---

### Post by bapoumba on 2007-02-25
Hum, did this happen before?
Could you please post the full error message to **sudo aptitude update**?

---

### Post by m_vrik on 2007-02-27
bapoumba,
Sorry for the delayed response.  I made a mistake trying to load KeePassx password manager to my Dapper distro and didn't know how to fix it without wiping my HD and reinstalling 6.06.  So, for now the problem is moot.  Now, I have to go back and reinstall the various repositories.  I don't think that I will try to install KeePass again as I was having difficulty integrating it with the clipboard daemon and the Fill extension.  Thanks for your response to my post.

---

