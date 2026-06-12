---
title: "Can't install programs"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by Big_J on 2006-08-19
My synaptic package manager doesn't load, the Add/Remove program loads, but doesn't install anything, the update manager shows that there are updates, but when I click install updates it just refreshes. 
Any ideas?

I can install using downloaded .deb files, I can use apt-get in a terminal, but no luck with the graphical installers.
I tried restarting x, rebooting, no luck, Synaptic just won't load up at all!
the last thing I installed was XGL and Compiz, and no xgl is not running right now, I set up differnet sessions. 

using ubuntu 6.06

---

### Post by mlind on 2006-08-19
If you launch synaptic or update-manager from terminal, does either print out any error messages?

---

### Post by Big_J on 2006-08-19
Yes

> 
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory


> bigj@Condor3:~$ whereis libvte.so.4
libvte.so: /usr/lib/libvte.so.9


---

### Post by mlind on 2006-08-19
Try reinstalling libvte4 package which is dependecy for synaptic. It looks to be broken..
```

sudo aptitude reinstall libvte4

```

---

### Post by Big_J on 2006-08-19
> Writing extended state information... Error!
E: I wasn't able to locate file for the libvte4 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?


How do I fix it manually?

---

### Post by mlind on 2006-08-19
> **Big_J said:**
> How do I fix it manually?

Strange error message... Close any other processes that might lock APT package database (synaptic, apt-get aptitude, adept, etc..)

Then run
```

sudo aptitude update
sudo aptitude reinstall libvte4

```

Post contents of **/etc/apt/sources.list** too.

---

### Post by Big_J on 2006-08-19
no luck, I'm gonna reboot and try again.

sources.list:
> 
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main


/edit
still no luck

---

### Post by mlind on 2006-08-19
Post complete output of invoking aptitude install and the resulted error.

Does *aptitude show libvte4* display the package information?

This can also be caused by corrupted APT database or problem in file that holds aptitude's "extended package state information". Hopefully not.

---

### Post by Big_J on 2006-08-19
> bigj@Condor3:~$ sudo aptitude reinstall libvte4
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  libvte4 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the libvte4 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
bigj@Condor3:~$ 


I also tried in the root terminal, same thing

And here's is the show info:
> bigj@Condor3:~$ aptitude show libvte4
Package: libvte4
State: installed
Automatically installed: no
Version: 1:0.13.5-0ubuntu2
Priority: optional
Section: libs
Maintainer: Guilherme de S. Pastore <gpastore@debian.org>
Uncompressed Size: 1425k
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2),
         libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.2), libglib2.0-0 (>=
         2.10.0), libglitz1 (>= 0.5.1+cvs20060213), libgtk2.0-0 (>= 2.8.0),
         libice6, libncurses5 (>= 5.4-5), libpango1.0-0 (>= 1.12.3), libpng12-0
         (>= 1.2.8rel), libsm6, libx11-6, libxcursor1 (> 1.1.2), libxext6,
         libxfixes3, libxft2 (> 2.1.1), libxi6, libxinerama1, libxrandr2,
         libxrender1, zlib1g (>= 1:1.2.1), libvte-common (= 1:0.13.5-0ubuntu2)
Description: Terminal emulator widget for GTK+ 2.0 - runtime files
 The VTE library inserts terminal capability strings into a trie, and then uses
 it to determine if data received from a pseudo-terminal is a control sequence
 or just random data. The sample program "interpret" illustrates more or less
 what the widget sees after it filters incoming data.


---

### Post by mlind on 2006-08-19
Does file /var/lib/aptitude/pkgstates states exist? This file could be corrupted, but don't do anything for it just yet.
Does file /var/backups/aptitude.pkgstates.0 or .1, .2 .3, etc. exist? There should be backup for /var/lib/aptitude/pkgstates file that could fix this issue.

I think you should post this to Ubuntu bugtracer [https://launchpad.net/distros/ubuntu/+source/aptitude/+bugs](https://launchpad.net/distros/ubuntu/+source/aptitude/+bugs), so that devs could give you more insighful help on this.

---

### Post by BARlotta on 2006-08-19
I was having the same issue.  I belive the Xgl/Compiz latest update may have caused the issue.

To fix (at least until a real fix comes out):

cd /usr/lib
sudo ln -s libvte.so.9 libvte.so.4

This makes a symbolic link from libvte.so.4 to libvte.so.9 (which is itself a link to libvte.so.9.1.2)

HTH,
Tim

---

### Post by Big_J on 2006-08-19
Thanks.

there's pkgstates and pkgstates.old, should I backup pkgstates and remove the .old from the old one?

---

### Post by Big_J on 2006-08-19
> I was having the same issue. I belive the Xgl/Compiz latest update may have caused the issue.

To fix (at least until a real fix comes out):

cd /usr/lib
sudo ln -s libvte.so.9 libvte.so.4

This makes a symbolic link from libvte.so.4 to libvte.so.9 (which is itself a link to libvte.so.9.1.2)

HTH,
Tim
Thanks, that did it

---

### Post by BARlotta on 2006-08-19
Glad to help!

---

### Post by Big_J on 2006-08-19
that fixes the problem by linking to 9, but that means I still can't reinstall 4
this is from pkgstates

> Package: libvte4
Unseen: no
State: 1
Dselect-State: 1
Last-Change: 0
Remove-Reason: 0
Anyone without compiz can confirm the values?

---

### Post by mlind on 2006-08-19
> **Big_J said:**
> that fixes the problem by linking to 9, but that means I still can't reinstall 4
this is from pkgstates


Anyone without compiz can confirm the values?

I have exact same values. Did you file a bugreport for this already?
If you want to experiment, backup your current pkgstates file and try backups from /var/backups folder. Most backups are gzipped, so you need to gunzip the archive first.

---

### Post by kodachrome64 on 2006-08-20
I'm having the same problem but w/ a different package.

Errors I get when trying to install using (aptitude). 

E: I wasn't able to locate file for the mfc4800lpr package. This might mean you need to manually fix this package.
E: Could't lock the list directory..are you root?

Errors I get when starting (Synaptic Package Manager).

E: The package mfc4800lpr need to be reinstalled, but I can'r find an archive for it.
E: internal error opening cache (1). Please report.

mfc4800lpr is a printer driver I installed. I downloadded the file and installed from the terminal. It is currently on my desktop (mfc4800lpr-1.1.2-1.i386.deb)

I'm not sure how to fix this based on the info provided in the previous posts. Can anyone explain what I can do for my situation.

---

### Post by mlind on 2006-08-20
> **kodachrome64 said:**
> I'm having the same problem but w/ a different package.

Errors I get when trying to install using (aptitude). 

E: I wasn't able to locate file for the mfc4800lpr package. This might mean you need to manually fix this package.
E: Could't lock the list directory..are you root?

Errors I get when starting (Synaptic Package Manager).

E: The package mfc4800lpr need to be reinstalled, but I can'r find an archive for it.
E: internal error opening cache (1). Please report.

mfc4800lpr is a printer driver I installed. I downloadded the file and installed from the terminal. It is currently on my desktop (mfc4800lpr-1.1.2-1.i386.deb)

I'm not sure how to fix this based on the info provided in the previous posts. Can anyone explain what I can do for my situation.

You should report this bug to launchpad, so that Ubuntu dev's can help you.
I would probably try to purge that package and then reinstall it
```

sudo dpkg -P --force-depends mfc4800lpr
sudo dpkg -i mfc4800lpr-1.1.2-1.i386.deb

```

---

