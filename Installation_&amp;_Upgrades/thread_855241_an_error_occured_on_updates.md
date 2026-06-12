---
title: "an error occured on updates"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by briancb on 2008-07-10
After trying running the script to install medibuntu in software sources I now have this error and cannot update anything.


E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Unable to lock the list directory

also

E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

what do I do?:confused:

---

### Post by jrasmussen0 on 2008-07-10
Can you copy the contents of your /etc/apt/sources.list ?

---

### Post by briancb on 2008-07-10
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main universe

---

### Post by briancb on 2008-07-10
This is what I get when I try to update:

---

### Post by briancb on 2008-07-10
Better this:

---

### Post by briancb on 2008-07-10
This is what I placed in terminal it caused all the problems:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list 

I was following the instructions at:

[http://www.zaphu.com/2008/05/30/ubuntu-guide-installing-media-codecs-for-flash-dvd-quicktime-mov-mp3-wmv-wma-and-acc-mp4-m4a-playback/](http://www.zaphu.com/2008/05/30/ubuntu-guide-installing-media-codecs-for-flash-dvd-quicktime-mov-mp3-wmv-wma-and-acc-mp4-m4a-playback/)

I tried to correct the problem by deleting anything that refered to medibuntu. 

Hope this helps someone to sort my problem please.

---

### Post by avtolle on 2008-07-10
Did you also add the GPG key? See [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories) for information.

---

### Post by briancb on 2008-07-10
I started again using the links on the page you directed me to and this solved the problem thank you.

---

### Post by briancb on 2008-07-10
Now I have the problem that my important security updates in sources will not accept a tick

---

### Post by avtolle on 2008-07-10
Yes, that's a bug that has been talked about on this Forum. It appears that you have the security repository enabled, so there should not be any problem with you receiving security updates (I got some yesterday, IIRC, and I don't have the security sources thing ticked, nor can I do so).

---

### Post by briancb on 2008-07-11
Thank you again

---

