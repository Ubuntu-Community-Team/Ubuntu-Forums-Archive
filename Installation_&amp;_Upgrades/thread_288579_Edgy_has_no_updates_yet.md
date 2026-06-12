---
title: "Edgy has no updates yet?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Zdravko on 2006-10-30
After distribution upgrade from Dapper to Edgy I get the following thing, when I search for updates for Edgy:
[[img=http://img209.imageshack.us/img209/6563/screenshotsoftwareupdatib8.th.png]](http://img209.imageshack.us/my.php?image=screenshotsoftwareupdatib8.png)


Is it normal, that there aren't any updates for Edgy yet?

---

### Post by rbalfour on 2006-10-30
Nay-sayer! BOO! lol.

IT's a good thing that there are no core system updates. Don't worry, the updates will comes, Let's hope that the updates are far and few.

---

### Post by Zdravko on 2006-10-30
Ok, but is it normal that there are 2 "already-installed" packages? Why are these "gray"/"disabled"?

---

### Post by rbalfour on 2006-10-30
It has to do with access to the repos. Have you enabled all repos.
Did you add non-ubuntu dapper repos to you sources.list? If so, you will need to update those entires.

---

### Post by Zdravko on 2006-10-30
Hm, strange. Here are the options in synaptic:

[[IMG]http://img207.imageshack.us/img207/4998/screenshotsoftwaresourcmz5.th.png[/IMG]](http://img207.imageshack.us/my.php?image=screenshotsoftwaresourcmz5.png)

How do I know if there is something wrong with my sources.list?

---

### Post by lazyd2 on 2006-10-30
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Zdravko on 2006-11-03
I got the following:
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse



---

### Post by jocko on 2006-11-03
to install the upgrades that are greyed out in update-manager, run this in a terminal: ```
sudo aptitude dist-upgrade
``` it looks like you still have some dapper packages installed.

---

### Post by Zdravko on 2006-11-03
Thanks, [jocko]("http://ubuntuforums.org/member.php?u=52751"), it worked. But I still don't get any updates for Edgy. Is this normal?

---

### Post by Max_Might on 2006-11-03
if you have finished with the "sudo aptitude dist-upgrade" you already have the newest version of Ubuntu :)

Enjoy ;)

---

### Post by Zdravko on 2006-11-03
Nope, I got 3 importnat security updates for Edgy:
libmagick9
libpq4
screen

---

