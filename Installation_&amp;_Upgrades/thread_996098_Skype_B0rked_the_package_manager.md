---
title: "Skype B0rked the package manager"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by pentium on 2008-11-28
I was attempting to upgrade the version of skype on my system (the older version was having trouble detecting an audio input device) when something screwy happened and now apt-get, the package manager and the update manager all error out with:
```
 The package skype needs to be reinstalled, but I can't find an archive for it.

```
...and I can't continue. Even logging out and restarting does not clear the problem and it's completely crippled the system (update and package management-wise). What are the steps I should take to fix the problem?

---

### Post by forkandles on 2008-11-28
If you can still access the terminal,type

sudo apt-get install skype

It is possible you may have to remove the earlier version of Skype FIRST by typing in terminal

sudo apt-get remove skype

---

### Post by pentium on 2008-11-28
Both commands still give me the same error.

```
 The package skype needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by forkandles on 2008-11-29
pentium,
I am assuming that Synaptic is still working okay. It should be, otherwise you really are in trouble!

Enter Synaptic and search for aptitude, then download and install it (select aptitude for installation,make,make,apply,apply). Just being thorough-no offence intended.

Now close Synaptic and go to terminal.
It is your choice whether you try to remove the old version of Skype first or just install the new version. I think you should try removal first just in case the old version has left some nonsense behind.

Using aptitude instead of apt-get, type

sudo aptitude remove skype

sudo aptitude install skype

For a comparison of aptitude and apt-get look here.

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

Good luck.

---

### Post by pentium on 2008-11-29
None of that works either. I can't do anything at all with any of the package mamagers without it giving the same error.

---

### Post by forkandles on 2008-11-29
pentium,

If nobody else comes up with a fresh idea soon, then I suggest you copy all your essential data (including Bookmarks and email profile directory) to a flash drive such as a Corsair Voyager and do a new installation of 8.10 or whatever you use.

Before you do so, double check that the saved data copies back correctly!!

---

### Post by oldos2er on 2008-11-29
pentium, can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by lswest on 2008-11-29
I would follow the instructions here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and add the medibuntu repo (which is where there's a skype deb) and see if that solves the problem.

---

### Post by pentium on 2008-11-29
Here you go.

```
deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty universe
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

```

Also, I am planning to switch to a completely new system soon as this one can't use more than 512Mb ram and is stuck with an ailing AGP card and 1Ghz processor. The new system however still needs an SATA drive and a (Nvidia preferred because I like their driver) PCI Express video card.

---

### Post by markbuntu on 2008-11-29
This happened to me once, not with skype but a broken graphics driver. But it was exactly the same symptoms. I was tearing my hair out, it was a bad nightmare.
Try this:

Open Synaptic, choose the bad skype package and then go to Package/Force Version and choose the previous version. Synaptic will remove the bad package and then everything should work again. 

It was the only thing that worked for me, I was about 2 minutes away from a clean reinstall when I found that.

Is this a bug or a feature?

---

### Post by pentium on 2008-11-30
I can't do anything with Synaptic.
I fire it up, it gives me the error and then closes. :mad:

---

### Post by oldos2er on 2008-11-30
I think Feisty's no longer supported, which means its repositories are no longer maintained. Maybe someone else could verify this?

---

### Post by pentium on 2008-11-30
Yeah, it's pretty old but with this system I can't go any further as the memory usage would be too great and from a graphical standpoint this system will lose its usefulness.

---

### Post by lswest on 2008-11-30
> **pentium said:**
> Yeah, it's pretty old but with this system I can't go any further as the memory usage would be too great and from a graphical standpoint this system will lose its usefulness.

Have you tried adding the medibuntu repositories for feisty?  Skype isn't in the actual repositories i don't think, so adding Medibuntu's repositories should allow apt-get to install the proper package.

Give it a shot?
Lswest

---

### Post by oldos2er on 2008-11-30
There are many Linux distros that are more suitable for older/less RAM systems.

---

### Post by pentium on 2008-11-30
Bah, I'll just live with this older version of Skype for a few more weeks, then I'll switch over to a new system and this one will be returned to duty as a rendering box with an old Intergraph Wildcat 3000.

---

### Post by soulspit on 2010-09-15
I got totally b0rked, so to speak, by Skype as well, after trying to install the lucid amd64 deb from Skype's website.  I don't remember but I think what happened was that I lost internet halfway through the install and it couldn't recover.  Moving the package file or downloading the newest deb from skype didn't work (it gave me permissions errors).  I had all the same problems the OP had.  I tried lots of things (though I didn't try the Force Version method mentioned in a post above) but I think what finally fixed it was adding the Skype repository (as detailed [here]("http://stream-recorder.com/forum/install-skype-repostiory-ubuntu-10-04-lucid-t6509.html")) and installing skype as it says (though I used aptitude instead of apt-get - apt-get wasn't working for it).  All problems seem solved!  I was damn near re-installing, too.  Just thought I'd post this here in case anyone else has this problem.

---

