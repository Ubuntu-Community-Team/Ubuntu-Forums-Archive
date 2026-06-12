---
title: "Nothing will install - Synaptic"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by SBro on 2005-09-21
Trying to install some things using the synaptic package manager, after I mark the packages I want to upgrade/install and then goto apply, the terminal pops up everytime with the same error.

"dpkg: failed to malloc for info file `/var/lib/dpkg/available': Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)"

Seems to happen for every package I try, can anyone tell me why this is happening and how to fix it? thanks guys.

---

### Post by John.Michael.Kane on 2005-09-21
May help to give us some system spec's...  since your error is saying you have mem issues..

---

### Post by SBro on 2005-09-21
P4 3.0Ghz, 512MB RAM, 160GB HDD - 8GB partition where Ubuntu lies (more then half that free disk space). Dual Boot (XP - Ubuntu), umm anything else you want to know? thanks.

---

### Post by John.Michael.Kane on 2005-09-21
try rebooting the machine and using synaptic again. also can you use the ubuntu update manager, and what repo's do you have in your souces.lst..

---

### Post by SBro on 2005-09-21
Rebooting doesn't seem to work, I went into the update manager, and had 376 packages to install, downloaded them all fine, as it's installing I get a terminal window popup saying:

"Extracting templates from packages: 100%
Preconfiguring packages..."

The window then sits there for about 5 seconds, then the terminal window closes...I'm guessing nothing is installed however, as I then reload the software updates window and the same 376 packages are listed again.

---

### Post by John.Michael.Kane on 2005-09-21
Thats very odd, can you check to see what repo's you have..

---

### Post by SBro on 2005-09-21
This is what is listed under my repositories.

CD Ubuntu 5.04 "Hoary Hedgehog" (Binary)
    URI: cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/

Ubuntu 5.04 "Hoary Hedgehog" (Binary)
    URI: [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu)

Ubuntu 5.04 "Hoary Hedgehog" (Source)
    URI: [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu)

Ubuntu 5.04 Security Updates (Binary)
    URI: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

Ubuntu 5.04 Security Updates (Source)
    URI: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

---

### Post by John.Michael.Kane on 2005-09-21
this my souce list copy and past it in your list and remove the cd repo you have Open a terminal and type: sudo gedit /etc/apt/sources.list replace all that in that file with what is posted here.. 

```
## Uncomment the following two lines to fetch updated software from the network
 deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by SBro on 2005-09-21
Did as you suggested and replaced my sources list with yours.  Went back in to package manager, got some sort of 'stat' error about the sources, then went into update manager, the same 376 packages still need to be installed, when I click install the same thing happens as before, no change. When I go back into package manager now, the 'stat' error is no longer there, but the same problems remain with not being able to install anything.  Beginning to think I need to re-install Ubuntu  :???:

---

### Post by John.Michael.Kane on 2005-09-21
yes i would say that you should do a clean install. sorry i could not be of more help..

---

### Post by az on 2005-09-22
Okay, from a command line try

sudo dpkg --clear-avail

to see if that can help.  Tell me what error that spits out.  Also, the next time you reboot, try running memtest86 (it is in your grub menu)

It may also be that you have a corrupt filesystem.  If dpkg is corrupt, then you cannot install stuff.  You can try reinstalling dpkg from a chroot, but that is complicated...

---

### Post by jamespi on 2006-05-16
hi, i have the same problem

i tried the clearavail thing above, i have fscked my hard drive so no corruption there - i think the problem may have been caused by me running dapper beta and updating it every day - the last update prevented my laptop from shutting down, so i just switched it off. since then dpkg won't work. always give me "malloc failed".

can you point me to an howto on manually installing dpkg.

thanks
james

---

### Post by jamespi on 2006-05-17
hi,

false alarm - "malloc failed" error is caused by a corrupt /var folder, and learning how to use fsck properly put me on the road to sorting out the error.

full details here:

[http://www.ubuntuforums.org/showthread.php?p=1025464#post1025464](http://www.ubuntuforums.org/showthread.php?p=1025464#post1025464)

---

