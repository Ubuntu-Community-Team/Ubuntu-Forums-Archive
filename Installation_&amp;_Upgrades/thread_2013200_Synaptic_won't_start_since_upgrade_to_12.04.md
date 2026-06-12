---
title: "Synaptic won't start since upgrade to 12.04"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by rbjscv on 2012-06-30
Just upgraded from 10.04 to 12.04 

Now Synaptic begins startup and then I get this:

E: The value 'lucid' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

My only choice is to click 'close'  and synaptic shuts down.

How can I fix it?  I'm guessing it has to do with leftover stuff from Lucid.  I've tried removing Syanptic, purging it, reinstalling it, searching for the word 'lucid' - all to no avail.  I'm in over my head.

Thanks for your help.

---

### Post by Karlchen on 2012-06-30
Hello, rbjscv.

Search the file /etc/apt/sources.list for occurrences of the string "lucid". Either replace "lucid" by "precise" or comment out such lines.

If you are unsure, please, post the content of your file /etc/apt/sources.list.

Kind regards,
Karl

---

### Post by cwsnyder on 2012-06-30
I'm going to assume from what you have stated that you are running Ubuntu 12.04, not Xubuntu, Lubuntu, or one of the other alternatives, and that you performed an upgrade-in-place rather than re-installing from disk.

The quick fix, assuming you have either a separate /home partition or have backed up your /home directory would be to install Ubuntu from CD.  This would remove any PPAs and other left-overs from Lucid, *and would remove Synaptic*.  Ubuntu 12.04 removes Synaptic and depends on the Software Center (or command line) to install/remove packages.  Xubuntu and Lubuntu continue to maintain Synaptic.

Alternatively, open Software Center, select the **Edit** menu item, then **Software Sources . . .**, then the **Other Software** tab and make sure that you have no PPAs which list Lucid as the version of Ubuntu supported.  You may _try_ simply replacing any instance of Lucid in the PPA with Precise and see if your PPAs have been updated.

You may also try editing the /etc/apt/sources.list directly (remember you will need sudo), but take care.

---

### Post by rbjscv on 2012-06-30
Here's the contents of my \etc\apt\sources.list file:

deb [http://le-web.org/repository](http://le-web.org/repository) stable main
deb [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) precise main universe multiverse restricted
deb-src [http://ubuntu.mirror.frontiernet.net/ubuntu/](http://ubuntu.mirror.frontiernet.net/ubuntu/) precise main universe multiverse restricted #Added by software-properties


And that's the whole sources.list file.  I can't help but think this has to do with leftover Lucid files.

---

### Post by cwsnyder on 2012-06-30
Have you tried commenting out the le-web.org line and rechecking?  This is a third-party repository and may be causing the problem.

---

### Post by rbjscv on 2012-06-30
I tried commenting out the le-web.org line.  Synaptic installs, but still displays the 'lucid' error.

---

### Post by cwsnyder on 2012-06-30
The following is my (VirtualBox) Xubuntu 12.04 /etc/apt/sources.list: ```
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```Don't know if this helped, but Synaptic works fine on my (virtual) Precise box.

---

### Post by rbjscv on 2012-06-30
cwsnyder,  I tried your sources list and I still got no joy.  So far nothing has worked and my frustration with Precise is growing to the point that I'm ready to revert to Lucid.  

I would still like to solve this and stay current rather than have a machine that would be out of date.

---

### Post by rbjscv on 2012-06-30
Also have searched my entire hard drive for 'lucid.'  All that was found were fonts that began with 'lucid.'

---

### Post by oldos2er on 2012-06-30
There's nothing "lucid" in /etc/apt/sources.list.d/ ?

Check [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/978821](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/978821)
although it's for oneiric and not lucid. In post #8 there may be a solution for you.

---

### Post by rbjscv on 2012-06-30
Read the bugs @ launchpad and 'lucid' didn't appear in any of the files mentioned.  But 'lucid' doesn't appear anyway in my file system.

---

### Post by rbjscv on 2012-07-18
I have been through everyfile on my machine to find the cause of this when Synaptic starts up:

E: The value 'lucid' is invalid for APT Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

Double colons go between APT and Default but I keep getting a smiley emoticon and I can't seem to turn them off.

Also I've searched the forum high and low and been through all the known bugs - all to no avail. Tried removing and reinstalling. And have checked and rechecked the sources.list file.  Nothing has made a difference.  Maybe if someone could explain what's going on here, I might be able figure out how to correct the problem.

Thank you for taking the time to read this.

rbjscv

---

### Post by asgekar on 2012-08-26
try to remove directory  /root/.synaptic

```
sudo \rm -fr /root/.synaptic
```

perhaps there are errors in the configuration files of synaptic... it cleared this error for me.

---

