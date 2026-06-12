---
title: "cant install anyuodates or use synaptic"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2006-11-25
its like the package manager {synaptic} will not connect with the internet it wont download any packages
this is what happens everytime i click to reload button

it say the repository for new ,removed ,upgraded software packages
and underneath that in a progress bar
it says downloading file 1 of 18
and underneath that
it says download rate unknown
and underneath that
it says show progress of single file
then it sets still like that for about eight minutes and
then it comes back with a bunch of errors about timing out


this is what it says


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.




[http://us.archive.ubuntu.com/ubuntu/...y/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/...y/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...s/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/...s/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/...ion-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...y/Release.gpg:](http://security.ubuntu.com/ubuntu/di...y/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://www.getautomatix.com/apt/dists/edgy/Release.gpg:](http://www.getautomatix.com/apt/dists/edgy/Release.gpg:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
[http://www.getautomatix.com/apt/dist...ion-en_US.bz2:](http://www.getautomatix.com/apt/dist...ion-en_US.bz2:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
[http://www.getautomatix.com/apt/dist...ion-en_US.bz2:](http://www.getautomatix.com/apt/dist...ion-en_US.bz2:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Edit/Delete Message
this is what i get when i run "gksudo gedit /etc/apt/sources.list"

this one comes from terminal

(gedit:7090): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


this one comes from sources.list


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
Edit/Delete Message

---

### Post by skale on 2006-11-27
Never seen that one before.

Is your internet working?  try `ping -t 3 google.com`

---

### Post by Hachi-Roku on 2006-12-05
I have a similar problem...

I can surf the web. Pings to test DNS work.

apt-get does not work.


apt-get, synaptic, other terminal commands lead to trying to resolve a bogus IP addy that is 1.0.0.0

Been searching for a cure with no luck.

Anyone?

Jon

---

### Post by Hachi-Roku on 2006-12-05
Just found this...

[http://ubuntuforums.org/showthread.php?t=250149&page=2](http://ubuntuforums.org/showthread.php?t=250149&page=2)

seems to be a common problem with "GAY-Link" routers.


winge

Man, my D-link router is the worst thing ive ever bought in all of history.

/winge

Jon

---

### Post by Hachi-Roku on 2006-12-05
dudes, im heaps amped! i just got it all working.

so jimbean try this...

Put your ISP's DNS IP address's in system>admin>networking>DNS

I changed mine from the router address to the ISP ones and bang it works.
J

---

### Post by jimbean on 2007-03-06
ok i figured it out i think
i need to add a search domains address
it works for me

---

