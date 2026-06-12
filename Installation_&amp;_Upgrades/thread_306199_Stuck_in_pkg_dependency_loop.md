---
title: "Stuck in pkg dependency loop"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by deathbeaver on 2006-11-24
Forgive me, I'm new. I may not even know what I'm talking about.

I was trying to install new software, according to the documentation I needed to verify I had the newest GCC and related packages. I figured out how to use apt-get and the Synaptic package manager and began installing things until it would no longer let me. I now have the following problem.

root@login-desktop:/home/login# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is installed
  g++-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is installed
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is installed
  libstdc++6-4.1-dev: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I've tried removing and installing these packages with apt-get and the synaptic pkg manager but niether can fix this.

I have tried everything I can think of, (not much, I'm new)
And I cannot find any posts/articles from similar issues to this.
Help!! (please and thanks)

---

### Post by kerry_s on 2006-11-24
What are you using?(dapper,edgy)

Please post your /etc/apt/sources.list so we can see what your trying to install from.

My guess is your using dapper, you might be able to get past that if you add the edgy repo or just change where it says dapper to say edgy. I can not say it will work & you might mess it up even more. Make sure you back up your important stuff & just be ready for a reinstall.

---

### Post by deathbeaver on 2006-11-24
It's a fresh download/install. So it should be edgy.....right?
Clipped from /etc/apt/sources.list:
****************************************************************
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

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
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
*******************************************************************

This is for learning. So messing it up is not a problem. There is nothing but Linux on this system. Any/All suggestions anyone can think of would be welcome. I'd like to try and get this resolved without a reinstall as I will not learn anything from that. (and will likely end up where I am now :p  )

---

### Post by deathbeaver on 2006-11-24
Sub Question:

Will running "apt-get update" and "apt-get install" after an installion take care of missing/outdated packages?

---

### Post by kerry_s on 2006-11-24
Try turning on all the repos, take out the # in front of deb. then run> sudo apt-get update <in terminal or press reload in synaptic.

---

### Post by deathbeaver on 2006-11-24
I uncommented all of the # deb....  lines and ran "apt-get update" , "apt-get upgrade". I'm getting the same errors as before. "apt-get -f install" still will  not fix it.

In the Synaptic PKG Manager, I hit reload. It infomed me that the same 6 pkgs are still having problems.

When I try to reinstall these pkgs I either get a list of dependancies that looks like absolutely everything I have installed on the system, (in which case I cancel the operation) or it does not complain and SynPM quits and I have to reopen it. And find the same 6 pkgs are broken.

---

### Post by deathbeaver on 2006-11-24
Just so it's clear, these are the lines I uncommented:

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by deathbeaver on 2006-11-24
Thankyou for the helpful suggestions Kerry_S.
I have reinstalled. And everything back to normal.

---

