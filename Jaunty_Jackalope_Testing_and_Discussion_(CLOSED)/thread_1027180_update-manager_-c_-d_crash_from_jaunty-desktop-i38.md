---
title: "update-manager -c -d crash from jaunty-desktop-i386.iso (daily live)"
date: 2009-01-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TDFlanders on 2009-01-01
Hi there,

this seems like a fairly serious failure to me (like priority high). 

Bug #312364:

This report is public

update-manager crashed with SIGSEGV in PyErr_SetFromErrnoWithFilenameObject() 

Although I am not the most strict ubuntu enthusiast around either, I think I need to warn from the following:

Most of my confirmed bugs of update-manager during the 8.10 alfa's got outdated without becoming fix committed. The crashes became irreproducible during beta. Now I think I have a valid gdb backtrace. Just give it a look please and if it is not good just close it down right away. There is no point in leaving this untriaged until it fixes itself I think.

Cheers,

Thomas

---

### Post by TDFlanders on 2009-01-01
Hi,

This could be actually a duplicate from 8.10 beta. Can anyone tell me if this is probably the case or if the backtraces are not valid? 

I cannot provide any /var/log files for this. The reason is that both these crashes occurred on a live-cd and my swap is not big enough to download all dbgsym's and gdb, alleyoop, valgrind and valgrind and stuff. I also would need to update or debug network-manager first, since I only have wireless or mobile broadband access. Also I cannot #root dpkg-reconfigure -aup low, because I cannot reboot! I cannot possibly upload anything less than the minimal report and I did not save .x-session-errors or a log file for this.

It is not reproducible from hard disk. #root apt-get check is irrelevant for the aforementioned reason.

I post a copy: on the forum and one to Michael and Arnaud. (If this is not the right procedure, please tell me which exact steps to take next time.)

Thanks!

Thomas


<8.10 beta>

Bug #282426 reported by  tdflanders on 2008-10-13 (Activity log)
(undecided) Bug #282426:
This report is public
update-manager crashed with SIGSEGV [edit]

This bug report was marked for expiration 14 days ago. (find out why) 

<9.04 alfa 2>

Bug #312364 reported by  tdflanders on 2008-12-30 (Activity log)
(undecided) Bug #312364:
This report is public
update-manager crashed with SIGSEGV in PyErr_SetFromErrnoWithFilenameObject() [edit]

---

### Post by ShirishAg75 on 2009-01-02
As far as expiration goes, it happens if nobody answers or adds to a bug report, although its usually about 56 days or something that you get after you file a report.

---

### Post by ShirishAg75 on 2009-01-02
TFlanders, 
 saw your bug-report (finally)

As far as dbgsym files are concerned, you need to add the following to your /etc/apt/sources.list 

```


deb http://ddebs.ubuntu.com intrepid main restricted universe multiverse
deb http://ddebs.ubuntu.com intrepid-updates main restricted universe multiverse
deb http://ddebs.ubuntu.com intrepid-proposed main restricted universe multiverse
deb http://ddebs.ubuntu.com intrepid-security main restricted universe multiverse


```

Wherever it says intrepid, just replace it with jaunty there. 

Then do 

```

gpg --keyserver keyserver.ubuntu.com --recv-key 428D7C01

```

This link should be fruitful for you. 

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by TDFlanders on 2009-01-02
Hi there Shirish,

I do not know why you posted me this link. I already did that. Only I only used the first jaunty line, since the other reps are not working yet for jaunty:

[...]

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports universe main multiverse restricted

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-updates main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-proposed main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid-security main restricted universe multiverse

deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jaunty main restricted universe multiverse
# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jaunty-updates main restricted universe multiverse
# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jaunty-proposed main restricted universe multiverse
# deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jaunty-security main restricted universe multiverse

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

[...]

As for Der Pitty's key, I also did that and verified through software-properties-gtk long time ago. Anyway, you said 'finally' you saw the bug. Does it have something to do with the fact that I cannot make a gpg-key? I have asked this to Canonical, but we agreed that this is probably due to my email-service blocking this. I am looking now for a work-around for that problem.

root@thomas-laptop:/home/thomas# gpg --keyserver keyserver.ubuntu.com --recv-key 428D7C01
gpg: requesting key 428D7C01 from hkp server keyserver.ubuntu.com
gpg: key 428D7C01: "Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
root@thomas-laptop:/home/thomas# software-properties-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
could not open file '<type 'file'>'
root@thomas-laptop:/home/thomas# 

Thanks for the help!

Thomas

---

### Post by ShirishAg75 on 2009-01-02
TDFlanders, 
 Why do you have a mix of Jaunty and Intrepid sources in /etc/apt/sources.list . Its a bad bad idea having mixed repos afaik. 

Here's mine of Intrepid (as right now I'm in Intrepid)

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

#dbgsym files 
deb http://ddebs.ubuntu.com intrepid main restricted universe multiverse
deb http://ddebs.ubuntu.com intrepid-updates main restricted universe multiverse
deb http://ddebs.ubuntu.com intrepid-proposed main restricted universe multiverse
deb http://ddebs.ubuntu.com intrepid-security main restricted universe multiverse

#PPA for transmission
# deb http://ppa.launchpad.net/chrisccoulson/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/chrisccoulson/ubuntu intrepid main

```One way to do things is to comment out using # as I have done just in case you want to go back to using Intrepid or something like that.

At my end things work out fine with the same on Intrepid as far as installation of -dbgsym files are concerned. 

```

$ aptitude search python-gobject
i   python-gobject                  - Python bindings for the GObject library   
p   python-gobject-dbg              - Python bindings for the GObject library (d
p   python-gobject-dbgsym           - debug symbols for package python-gobject  
p   python-gobject-dev              - Development headers for the GObject Python
v   python-gobject-doc              -         

$ aptitude show python-gobject
Package: python-gobject
State: installed
Automatically installed: no
Version: 2.15.3-0ubuntu5
Priority: optional
Section: python
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1114k
Depends: python (< 2.6), python (>= 2.4), python-support (>= 0.7.1), python2.5
         (>= 2.5.2-5), libc6 (>= 2.4), libffi5 (>= 3.0.4), libglib2.0-0 (>=
         2.16.0)
Suggests: python-gobject-dbg
Conflicts: python-gtk2 (< 2.10)
Provides: python2.4-gobject, python2.5-gobject
Description: Python bindings for the GObject library
 GObject is an abstraction layer that allows to program with an object paradigm
 that is compatible with many languages. It is a part of Glib, the core library
 used to build GTK+ and GNOME. 
 
 This package contains the Python bindings for GObject. It is mostly used by
 other bindings to map their GObjects to Python objects.

```


```

$ sudo aptitude install python-gobject-dbgsym
[sudo] password for shirish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  python-gobject-dbgsym 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 480kB of archives. After unpacking 1475kB will be used.
Writing extended state information... Done
Get:1 http://ddebs.ubuntu.com intrepid/main python-gobject-dbgsym 2.15.3-0ubuntu5 [480kB]
Fetched 480kB in 14s (32.4kB/s)                                                 
Selecting previously deselected package python-gobject-dbgsym.
(Reading database ... 113120 files and directories currently installed.)
Unpacking python-gobject-dbgsym (from .../python-gobject-dbgsym_2.15.3-0ubuntu5_i386.ddeb) ...
Setting up python-gobject-dbgsym (2.15.3-0ubuntu5) ...
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

---

### Post by TDFlanders on 2009-01-05
Hi there Sirish,

I seriously appreciate the dedicated and fast help, but I fear that we are talking next to each other here. I only mentioned the dbgsym's as not being feasible to do this on a live cd due to disk space (swap). More important still is that I cannot reconfigure and reboot as I am working on a live cd and so rebooting will not preserve any changes. I know how to activate the repos. The mixed repos arise in fact from upgrading from 8.10 to 9.04 through root# update-manager -c -d. Anyway, don't break your head over it, 

I will ask now on launchpad digest if anyone can take a look at the bug reports, so the bugs can get triaged, or can you do that? I have gdb backtraces, so I can mark them confirmed, but that does not mean the developers will be notified, right?

Cheers,

Thomas

---

### Post by marmuta on 2009-01-05
TDFlanders, if you don't have enough ram/swap to install things on the livecd, 
you could try to redirect /usr to your hard drive. This might just work on the livecd too.

```
mkdir hd
sudo mount /dev/sdaX hd
mkdir hd/aufs_rw
sudo mount -t aufs -o dirs=~/hd/aufs_rw=rw:/usr=ro myunion /usr

```

Everything new you write to /usr should go to hd/aufs_rw from then on and not take up ram.

---

