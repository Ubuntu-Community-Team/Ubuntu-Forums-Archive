---
title: "Cannot update software sources"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by chejose on 2007-10-21
My instalation of 7.10 is working fine, except for one thing: I cannot install any programs.

If in System/Administration/ Software sources I mark one of the categories, The "download package information" gets to 7, and stops. I can mark any of the categories, and the same happens.

The result is that programs I want to install, such as Gnome Commander and K3d will not install. If I mark one of them to install, the "Download package installation" also gets to 7 and stops.

If I run "apt-get update", with any of the Software Sources selected, it gets to 66% and stops.

The programs I want to install were ones I was using in the previous version of Ubuntu, so it is not a problem of the PC.

There must be an answer... I do not want to have to go back to the earlier version.

Thanks for any help... and please make it at the level of a fairly new Linux user.

José

---

### Post by Pumalite on 2007-10-21
copy and paste here the output of:
sudo apt-get install k3b

---

### Post by chejose on 2007-10-21
Thanks for getting on this. Here is the result.

jose@josey:~$ sudo apt-get install k3b
[sudo] password for jose:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package k3b

José

---

### Post by chejose on 2007-10-21
Sorry. It should have been k3d, but the result is the same.

---

### Post by Pumalite on 2007-10-21
Post:
cat /etc/apt/sources.list

---

### Post by chejose on 2007-10-21
Here is the list. I had "un commented" some of them, but the update would always hang at 7. So I made them all comment again. I note that a number of lines "failed to verify" which could be, or be part of, the problem.

jose@josey:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
## deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Pumalite on 2007-10-21
This way you have nothing to download from. Uncomment the repos.(deb...etc)

---

### Post by chejose on 2007-10-22
Right, that is the logical step. But as I said in the earliest note, apt-get update gets so far, and stops. I tried un-commenting items from different blocks, but always the same.

This time I un-commented two items from the first block. The update got to 46% an hung. It said it could not make the connection and timed out.

I have now tried to do the same more than once, and always the same happens. It gets so far and hangs. My internet connection is not the problem. This time in the morning I normally have around 300k download speed.

So something strange is happening, but so far I see no light.

So again, thanks for trying to help.

José

---

### Post by chejose on 2007-10-22
I just tried it again with the two canonical addresses, and as you can see:

jose@josey:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
50% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to us.archive.u
jose@josey:~$ 

There is the problem.

José

---

### Post by Pumalite on 2007-10-22
The servers are buzzy. Try changing mirrors. System>Administration>Software Sources>US to MAIN as an example.

---

### Post by chejose on 2007-10-22
OK.. I guess it is just a matter of patience. So thanks for taking the matter this far.

José

---

