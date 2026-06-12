---
title: "malformed line in source list"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by Monsoonx27 on 2006-11-21
Im a big noob and i dont know what this error means so
if you know how to fix this 

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

The package manager give me that message.

it would be really appreciated

---

### Post by Aranel on 2006-11-21
Post the contents of the file /etc/apt/sources.list. To do that, go to Applications > Accessories > Text Editor, go to File > Open, and select the corresponding file. Maybe then the issue can be diagnosed.

Edit: I misread your post... I guess I'm not positive what the problem is. But please do copy and paste the contents of your sources.list file, nevertheless.

---

### Post by Monsoonx27 on 2006-11-22
here is my sources.list file contents
i know i added alot of stuff to the top and thats the root of my problem

*******
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
deb [http://seveas.imbrandon.com/](http://seveas.imbrandon.com/) edgy-seveas extras seveas-meta custom
deb-src [http://seveas.imbrandon.com/](http://seveas.imbrandon.com/) edgy-seveas extras seveas-meta custom
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) edgy all
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) edgy all
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) edgy-cafuego all
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) edgy-cafuego all




deb [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy main
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by taurus on 2006-11-22
Can you try to reverse your /etc/apt/sources.list back to the original copy?  You did make a backup copy before you started editing your /etc/apt/sources.list, right!!!

---

### Post by Monsoonx27 on 2006-11-22
unfortunately i didn't make a back up but i can probably revert it back to its orgininal form as i only ammended to the top

---

### Post by taurus on 2006-11-22
If you want, I can paste here a copy that I use for my Edgy!

---

### Post by Monsoonx27 on 2006-11-22
that would be great if you could post it

---

### Post by taurus on 2006-11-22
> **Monsoonx27 said:**
> that would be great if you could post it
Okay, here goes...

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Monsoonx27 on 2006-11-22
yeah, no dice so i am prolly gonna reinstall thanks for your help though

---

