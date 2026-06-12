---
title: "How to update python"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by screaminj3sus on 2009-03-27
First of all why the hell is that broken python still in the freaking repos, I just updated and it destroyed everything.

My mirror does not have the updated python and I can't change the mirror because the software sources doesn't work anymore.. is there a mirror with the update and if so how can I use it? or can some one give me a deb or anything.

---

### Post by Sub101 on 2009-03-27
Have you tried another 
```
sudo apt-get update && sudo apt-get upgrade
```

Python broke for me this morning, then after a second update it fixed itself.

---

### Post by screaminj3sus on 2009-03-27
I just tried that 3 seconds before my post and now gain still the old package. whatever mirror I am using (I had synaptic choose the best) does NOT have it.

---

### Post by Aenima99x on 2009-03-27
> **screaminj3sus said:**
> I just tried that 3 seconds before my post and now gain still the old package. whatever mirror I am using (I had synaptic choose the best) does NOT have it.

I had the same problem, what I did to get around the problem was the following -
renamed sources.list to sources.list.backup (it's at /etc/apt/)
created a new sources.list with the following repositories only

```
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu/ jaunty main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted
```

the run sudo apt-get update
after you get all the updates, you can change back to your original sources.list

---

### Post by kansasnoob on 2009-03-27
It's now available at [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

You could see what your source is by running:

```
cat /etc/apt/sources.list
```

Here's mine:

> lance@lance-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse


---

### Post by Sub101 on 2009-03-27
Check the sticky [here]("http://ubuntuforums.org/showthread.php?t=1107854")

---

### Post by screaminj3sus on 2009-03-27
I am using the official repos now it was updating fine and now it can't connect to the damn repo! it went down during my update sp it couldn't finish. this crap is getting ridiculous

---

### Post by screaminj3sus on 2009-03-27
Need to get 21.6MB/70.6MB of archives.
After this operation, 651kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libglu1-mesa 7.3-1ubuntu4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main mesa-utils 7.3-1ubuntu4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-problem-report 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-apport 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main apport 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main apport-gtk 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main cups-bsd 1.3.9-16
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main cups-client 1.3.9-16
  404 Not Found [IP: 91.189.88.31 80]

---

### Post by smbm on 2009-03-27
Have you tried an 

```
apt-get clean
```

followed by an update and an upgrade.

I was getting various errors earlier and these actions fixed it.


P.S Your tone earlier in the thread comes off as quite aggressive.

---

### Post by cariboo on 2009-03-27
You may want to wait a while until trying to fix the problem, as the repos are very busy right now.

Jim

---

### Post by macogw on 2009-03-27
> **screaminj3sus said:**
> Need to get 21.6MB/70.6MB of archives.
After this operation, 651kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libglu1-mesa 7.3-1ubuntu4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main mesa-utils 7.3-1ubuntu4
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-problem-report 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-apport 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main apport 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main apport-gtk 0.146
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main cups-bsd 1.3.9-16
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main cups-client 1.3.9-16
  404 Not Found [IP: 91.189.88.31 80]

That's probably because the bad packages were pulled off of the repos.

---

### Post by macogw on 2009-03-27
> **screaminj3sus said:**
> First of all why the hell is that broken python still in the freaking repos, I just updated and it destroyed everything.
You posted two hours ago, but it was removed from the repos about 10 hours ago...Should just throw 404s.

---

