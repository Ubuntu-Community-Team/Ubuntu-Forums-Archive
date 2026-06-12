---
title: "Package Manager Issue"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by schmidtbag on 2008-06-07
Ubuntu has been working flawlessly for me for a long time.  Today I got a notification saying that Wine needed to be updated.  I told it to install the packages, but it never did.  The updater kind of just froze there doing nothing.  the "gksu" process was considered asleep.  I figured "hmm, maybe theres just an issue with the source so I'll go disable it for now".  Well, apparently System>Software Sources doesn't work either.  Then I got a little worried, so I started up Synaptic Package Manager, which also wouldn't start up.  The add/remove application starts up but I'm sure if I were to apply any changes, it won't.

Whats going on here?  I have no idea what caused this.  The last change I did to my computer was looking for ways to share files between a Windows computer, which btw I did not accomplish (I couldn't figure out how to change my workgroup).  But anyway, I don't see what that would have to do with my situation now seeing as how I didn't use any package manager to attempt to get file sharing to work.

Much thanks in advance.

---

### Post by abhiroopb on 2008-06-07
Have you tried restarting (YES sounds like IT Crowd, but it works sometimes!!)

---

### Post by schmidtbag on 2008-06-07
lol yes.  Right now I'm using module 2.6.24-18, and i tried 17 as well with no luck.

---

### Post by abhiroopb on 2008-06-07
Are you on hardy? Why are you changing kernels? Open a terminal and type sudo apt-get update.

---

### Post by schmidtbag on 2008-06-07
I am running Hardy but I'm not trying to change kernels, when I update, for some reason the old kernels aren't removed.  I'll get around to that later.


when I typed in sudo apt-get update I got this message at the end:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems


so, I tried typing in apt-get update and I got this:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


Now what?  BTW, thanks a lot for the quick responses

---

### Post by abhiroopb on 2008-06-07
no problem.

Type in:
```
gksudo gedit /etc/apt/sources.list
```

A file will open up, please paste its contents here.

Then try this in a terminal
```

sudo rm /var/lib/dpkg/lock 
sudo rm /var/cache/apt/archives/lock
sudo apt-get update

```

Let me know what happens.

---

### Post by schmidtbag on 2008-06-07
sources.list contents:

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Nothing seemed to happen with the other scripts you gave me.  It didn't say anything about the files being removed, but when I tried it again it said they were gone.  The update still doesn't go.

---

### Post by abhiroopb on 2008-06-07
The scripts I gave basically deleted the lock files. You are still getting the same lockfile error? Close ALL open windows/programs and try it.

---

### Post by schmidtbag on 2008-06-07
Ya I'm getting the same error but its not lockfile, its about me having 13 permissions denied.

BTW, if I try "sudo gksu /usr/sbin/synaptic", it starts up but I get this message:
sudo: unable to resolve host Tornado-II

(Tornado-II is the computer name fyi)
If I just type in "gksu /user/sbin/synaptic" then terminal just creates a space and the cursor keeps blinking but nothing happens.  So this is definitely related to permissions and that only.

---

### Post by abhiroopb on 2008-06-07
What I think what is happenin is that some file is locked, etc...not sure which one it is unfortunately :(

---

### Post by schmidtbag on 2008-06-07
well if i just removed every locked file, if i'm able to run these apps under SU, and if its saying theres permission problems (which wouldn't surprise me when i was trying to do file sharing) then unless "locked" just means no permissions to anyone, then i just need to find a way to grant these permissions.

if there is a locked file somewhere and that is the issue, then couldn't i just unlock everything in the /var/lib/apt/ folder?

---

