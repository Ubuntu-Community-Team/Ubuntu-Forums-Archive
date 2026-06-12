---
title: "[SOLVED] synaptic and apt-get are gone"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by nomis3613 on 2008-06-17
Since I installed some audio software on my laptop, they have both disappeared, so I can't install any programs. How do I get them back?
```
sudo apt-get install normalize-audio
[sudo] password for general:
sudo: apt-get: command not found
```many thanks,
Simon

---

### Post by nomis3613 on 2008-06-20
Hello, can someone please help me out? I looked in /usr/bin and can't find apt-get either. I have tried to reinstall it myself but had no luck. At the moment, .deb files are being opened with archive manager.

Can someone please help, I am really stuck.

---

### Post by secondstage on 2008-06-20
This is coming from an Ubuntu user, not Xubuntu.

You could probably build synaptic from the source code and build it, but I would have no clue where to get the source. If you get no more responses, then I guess you would need to do a reinstall. I know that I shouldn't say that but it is the 'magical cure for all problems'

---

### Post by abn91c on 2008-06-20
did you try sudo aptitude reinstall adept-manager

---

### Post by nomis3613 on 2008-06-21
just tried the reinstall command then, "command not found" still...
thanks anyway. any more ideas before I reinstall?

---

### Post by PmDematagoda on 2008-06-21
Download the apt package from [here]("http://packages.ubuntu.com/hardy/apt") to your home directory.

Then open a terminal and execute:-
```
sudo dpkg -i name-of-deb.deb
```
and see if that brings apt-get back.

---

### Post by VMC on 2008-06-21
I'm sure PmDematagoda post will answer your question, but if you type from Terminal

```
locate apt-get
```

What shows up?

---

### Post by nomis3613 on 2008-06-21
Thanks for the help, I think we're close!
```
sudo dpkg -i apt_0.7.6ubuntu14_i386.deb
[sudo] password for general:
Selecting previously deselected package apt.
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb
```
I am using gutsy so I downloaded this version instead.

"locate apt-get" returned this
```
locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
```

What's the next plan of attack?

Thanks,
Simon
> **PmDematagoda said:**
> Download the apt package from [here]("http://packages.ubuntu.com/hardy/apt") to your home directory.

Then open a terminal and execute:-
```
sudo dpkg -i name-of-deb.deb
```
and see if that brings apt-get back.

---

### Post by PmDematagoda on 2008-06-22
The strange thing is that dpkg says that there is already another version of apt, what version of Ubuntu are you running?

---

### Post by nomis3613 on 2008-06-23
Strange indeed. I am running Xubuntu Gutsy. 

I got into this mess when I installed some audio software. Package installer warned me it was removing Synaptic, I thought it was very strange for an audio program to require this, but went ahead with it thinking maybe it would update it or install an alternative. Woops!

Any suggestions?
Thanks.

Edit: it was Exaile that caused apt to be removed

---

### Post by PmDematagoda on 2008-06-23
Since you have Gutsy, the apt package should be obtained from [here]("http://packages.ubuntu.com/gutsy/apt"). But what confuses me is why apt was removed during the Exaile install, which shouldn't happen at all.

---

### Post by nomis3613 on 2008-07-01
Thanks. How do I install the package? I tried it with dpkg, but got
```
general@simon-laptop:~/Desktop$ sudo dpkg -i apt_0.7.6ubuntu14_i386.deb
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb

```
PS Sorry for the delay, I was waiting for my housemate (who uses gentoo) to try to compile it for me, but that didn't work.

---

### Post by PmDematagoda on 2008-07-01
Hmm, then perhaps you can try and force it, but first an important thing, since apt is a rather critical package, you may want to backup any stuff you may want before forcing the install(or atleast keep a Live CD handy). Also are you sure that you have Gutsy? If so, then run:-
```
sudo dpkg -i --force-depends name-of-package.deb
```

---

### Post by nomis3613 on 2008-07-01
> **PmDematagoda said:**
> Hmm, then perhaps you can try and force it, but first an important thing, since apt is a rather critical package, you may want to backup any stuff you may want before forcing the install(or atleast keep a Live CD handy). Also are you sure that you have Gutsy? If so, then run:-
```
sudo dpkg -i --force-depends name-of-package.deb
```

Yeah, definitely running Gutsy. At some stage I might have been desperate and tried getting around the problem by installing the Hoary version. Whoops. Thanks for the tip, but it's still not happy unfortunately:
```
general@simon-laptop:~/Desktop$ sudo dpkg -i --force-depends apt_0.7.6ubuntu14_i386.deb 
[sudo] password for general:
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb

```

---

### Post by PmDematagoda on 2008-07-01
That's even weirder, all right, try this:-
```
sudo dpkg -i --force-all apt_0.7.6ubuntu14_i386.deb 
```

---

### Post by nomis3613 on 2008-07-02
Progress!! apt is now installed. Thankyou sooo much. If you could just help me reinstall synaptic then I'll leave you alone...
```
general@simon-laptop:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
  synaptic: Depends: libapt-inst-libc6.7-6-1.1
            Depends: libapt-pkg-libc6.7-6-4.6
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by PmDematagoda on 2008-07-02
Hmm, this is really weird, can you post the output of:-
```
cat /etc/apt/sources.list
```
I think you might have a few defective repository entries.

---

### Post by nomis3613 on 2008-07-03
> **PmDematagoda said:**
> Hmm, this is really weird, can you post the output of:-
```
cat /etc/apt/sources.list
```
I think you might have a few defective repository entries.

Sure, here goes:
```
general@simon-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse web
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main restricted multiverse web
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted multiverse web
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ftp.au.debian.org/debian sid main
deb http://ftp.iinet.net.au/pub/ubuntu gutsy main universe
deb http://apt.wicd.net gutsy extras

```

---

### Post by PmDematagoda on 2008-07-03
Yep, there's your problem:-
```
deb http://ftp.au.debian.org/debian sid main
```
having Debian sources can cause these problems, just remove or uncomment the source by adding a # to the beginning and then do:-
```
sudo apt-get update
```
after that finishes, check if you can now install synaptic.

---

### Post by nomis3613 on 2008-07-04
the update was all going fine until here:
```
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
is this a problem, well I tried synaptic afterwards anyway but as you can see wimped out when I got an ominous warning about overwriting system files!

```
general@simon-laptop:~$ sudo synaptic
synaptic: error while loading shared libraries: libapt-inst-libc6.6-6.so.1.1: cannot open shared object file: No such file or directory

general@simon-laptop:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
  synaptic: Depends: libapt-inst-libc6.6-6-1.1
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
general@simon-laptop:~$ sudo synaptic
synaptic: error while loading shared libraries: libapt-inst-libc6.6-6.so.1.1: cannot open shared object file: No such file or directory
general@simon-laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

general@simon-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcwidget3 libxapian15 debian-archive-keyring libdb4.6
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apt synaptic
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt
0 upgraded, 0 newly installed, 2 to remove and 68 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 10.6MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 
Abort.
```
what should I do? 
thanks!

---

### Post by PmDematagoda on 2008-07-04
Try and remove Synaptic, and then try reinstalling it. But please look at any other packages its about to delete before going on.

---

### Post by nomis3613 on 2008-07-04
> **PmDematagoda said:**
> Try and remove Synaptic, and then try reinstalling it. But please look at any other packages its about to delete before going on.

ok, umm I got got stuck trying to remove synaptic. Here's what happened:
```
general@simon-laptop:~$ sudo apt-get remove synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
thanks for all your help! hopefully we're close to done here...

---

### Post by PmDematagoda on 2008-07-05
Ok, do:-
```
sudo apt-get install -f
```
and let it remove apt, since you have the install file you can reinstall it anyway.

---

### Post by Partyboi2 on 2008-07-05
You need to remove the web entries from your sources.list 
```
gksudo gedit /etc/apt/sources.list
```Look for all the lines that have [COLOR=Red]web[/COLOR] at the end of them and remove it.
So for example:
```
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted multiverse [COLOR=Red]web[/COLOR] 
```would become
```
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted multiverse 
``````
general@simon-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse [COLOR=Red]web[/COLOR]
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse [COLOR=Red]web[/COLOR]
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse [COLOR=Red]web[/COLOR]
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) sid main
deb [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) gutsy main universe
deb [http://apt.wicd.net]("http://apt.wicd.net/") gutsy extras
```After saving the changes
```
sudo apt-get update
```

---

### Post by nomis3613 on 2008-07-05
ok, here's my latest bumbling attempt! (After I got rid of "web" from my sources, as suggested.)
```
general@simon-laptop:~$ sudo apt-get update
[sudo] password for general:
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 http://ftp.iinet.net.au gutsy Release.gpg [191B]                                             
blah blah blah...
Fetched 5B in 3s (1B/s)  
Reading package lists... Done
```
Then I unsuccesfully tried removing/installing synaptic
```
general@simon-laptop:~$ sudo apt-get remove synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

general@simon-laptop:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
  synaptic: Depends: libapt-inst-libc6.6-6-1.1
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

general@simon-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcwidget3 libxapian15 debian-archive-keyring libdb4.6
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apt synaptic
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt
0 upgraded, 0 newly installed, 2 to remove and 68 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 10.6MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
(Reading database ... 99878 files and directories currently installed.)
Removing synaptic ...
Removing apt ...
```
Then I had to "force-all" install apt (same as before)
```
general@simon-laptop:~/Desktop$ sudo dpkg -i apt_0.7.6ubuntu14_i386.deb
Selecting previously deselected package apt.
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb

general@simon-laptop:~/Desktop$ sudo dpkg -i --force-depends apt_0.7.6ubuntu14_i386.deb
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb

general@simon-laptop:~/Desktop$ sudo dpkg -i --force-all apt_0.7.6ubuntu14_i386.deb
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: warning - ignoring conflict, may proceed anyway !
(Reading database ... 99549 files and directories currently installed.)
Unpacking apt (from apt_0.7.6ubuntu14_i386.deb) ...
touch: cannot touch `/var/lib/apt/lists/partial/.delete-me-later': No such file or directory
Setting up apt (0.7.6ubuntu14) ...
```
After this I tried updating and installing synaptic, but still getting the same errors
```
general@simon-laptop:~/Desktop$ sudo apt-get update
blah blah same as before 
Fetched 5B in 22s (0B/s)                                                                           
Reading package lists... Done

general@simon-laptop:~/Desktop$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
  synaptic: Depends: libapt-inst-libc6.6-6-1.1
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Any ideas?
Thanks.

---

### Post by PmDematagoda on 2008-07-05
It seems that the Sid repository has done it's damage, did you try doing apt-get install -f?

---

### Post by nomis3613 on 2008-07-05
> **PmDematagoda said:**
> It seems that the Sid repository has done it's damage, did you try doing apt-get install -f?

It wants to remove apt again. Should I do this? I don't understand what's going on here! Why would 'fixing' apt-get cause it to remove apt??
```
general@simon-laptop:~$ sudo apt-get install -f
[sudo] password for general:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcwidget3 libxapian15 debian-archive-keyring libdb4.6
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apt
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt
0 upgraded, 0 newly installed, 1 to remove and 68 not upgraded.
Need to get 0B of archives.
After unpacking 4551kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

```

---

### Post by PmDematagoda on 2008-07-05
It must be because of this:-
```
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
  synaptic: Depends: libapt-inst-libc6.6-6-1.1
```

Synaptic depends on apt, but apt works using some dependencies that the Ubuntu version of Synaptic doesn't like, so the fix is to remove apt and all it's dependencies and reinstall them again.

---

### Post by nomis3613 on 2008-07-05
> **PmDematagoda said:**
> It must be because of this:-
```
  dpkg: Conflicts: apt (< 0.7.7) but 0.7.6ubuntu14 is to be installed
  synaptic: Depends: libapt-inst-libc6.6-6-1.1
```

Synaptic depends on apt, but apt works using some dependencies that the Ubuntu version of Synaptic doesn't like, so the fix is to remove apt and all it's dependencies and reinstall them again.

Sure, I thought I'd reinstalled apt already- have I not reinstalled the dependencies properly? How do I do this? What version of apt should I install?
(sorry if you've already told me this, I'm a bit out of my depth here!)

---

### Post by PmDematagoda on 2008-07-06
> **nomis3613 said:**
> Sure, I thought I'd reinstalled apt already- have I not reinstalled the dependencies properly? How do I do this? What version of apt should I install?
(sorry if you've already told me this, I'm a bit out of my depth here!)

You did install apt, but since you had to force it to install it is now using incorrect dependencies and not the proper ones, so in order to completely fix the problem you will have to completely reinstall apt and all of it's dependencies from scratch. The dependencies you will want are [here]("http://packages.ubuntu.com/gutsy/apt").

---

### Post by nomis3613 on 2008-07-07
Thanks for your continued patience!
I installed the required dependencies:
```
general@simon-laptop:~/Desktop$ sudo dpkg -i libgcc1_4.2.1-5ubuntu4_i386.deb 
(Reading database ... 99549 files and directories currently installed.)
Preparing to replace libgcc1 1:4.2.1-5ubuntu4 (using libgcc1_4.2.1-5ubuntu4_i386.deb) ...
Unpacking replacement libgcc1 ...
Setting up libgcc1 (1:4.2.1-5ubuntu4) ...

general@simon-laptop:~/Desktop$ sudo dpkg -i libc6_2.6.1-1ubuntu9_i386.deb 
dpkg - warning: downgrading libc6 from 2.7-11 to 2.6.1-1ubuntu9.
(Reading database ... 99549 files and directories currently installed.)
Preparing to replace libc6 2.7-11 (using libc6_2.6.1-1ubuntu9_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.6.1-1ubuntu9) ...
Installing new version of config file /etc/init.d/glibc.sh ...
Installing new version of config file /etc/gai.conf ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

general@simon-laptop:~/Desktop$ sudo dpkg -i libstdc++6_4.2.1-5ubuntu4_i386.deb 
(Reading database ... 99546 files and directories currently installed.)
Preparing to replace libstdc++6 4.2.1-5ubuntu4 (using libstdc++6_4.2.1-5ubuntu4_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.2.1-5ubuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

But apt didn't want to install:
```
general@simon-laptop:~/Desktop$ sudo dpkg -i apt_0.7.6ubuntu14_i386.deb 
Selecting previously deselected package apt.
dpkg: regarding apt_0.7.6ubuntu14_i386.deb containing apt:
 dpkg conflicts with apt (<< 0.7.7)
  apt (version 0.7.6ubuntu14) is to be installed.
dpkg: error processing apt_0.7.6ubuntu14_i386.deb (--install):
 conflicting packages - not installing apt
Errors were encountered while processing:
 apt_0.7.6ubuntu14_i386.deb

```
Is dpkg itself causing a conflict? Reinstalling dpkg (through dpkg?) sounds tricky! Where to next, Boss?

---

### Post by PmDematagoda on 2008-07-07
I think you will have to force the apt install, so do:-
```
sudo dpkg -i --force-all apt_0.7.6ubuntu14_i386.deb
```
Perhaps dpkg is instructed such that it does not downgrade apt unless forced to do so since apt is obviously a quite important package.

---

### Post by nomis3613 on 2008-07-07
I'm in! Synaptic is installed. It doesn't work yet, but it's progress...

I had to install apt-utils, then I could apt-get install synaptic. Then synaptic ran. But my joy was short lived because if I mark ANY package for removal or installation, it comes up with a list of packages that need to be removed. This list seems like every package on my PC!
At the moment, these packages are showing with broken dependencies: dpkg, exaile (which I wanna get rid of anyway), libc6-i686, libcwidget3, libdatrie0, libdb4.6, libgcrypt11, libglib2.0-0, libgnome-keyring0, libncursesw5, libpango1.0-0, libselinux1, libzaplan15, python-pyogg, python-pysqlite2, python-pyvorbis.

I tried to update these packages, but the only options were removal- which would remove my whole system. I checked one of the packages and it is a newer version than gutsy. I can force install the gutsy version if that will help.

Also, I am getting this error in the terminal I ran synaptic through
```
(



 synaptic:28846): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

```
What should I do?
Thanks,
Simon

---

### Post by PmDematagoda on 2008-07-07
Well, when I had such a problem, there was only one way to fix it, download those packages manually from the proper locations for the proper release and then use dpkg to install them to replace the improper ones.

---

### Post by nomis3613 on 2008-07-10
> **PmDematagoda said:**
> Well, when I had such a problem, there was only one way to fix it, download those packages manually from the proper locations for the proper release and then use dpkg to install them to replace the improper ones.

Yay!!!!!!!!!!!!! Synaptic works!!!! All is fixed. I went through all the packages and downgraded them with dpkg. I was nervous about using dpkg to install dpkg, but it worked no problems.

Thankyou sooooo much for all your help and patience!

Simon

---

### Post by PmDematagoda on 2008-07-10
Glad it worked out for you:). May that be a lesson to be more careful about the repositories you use in the future:).

---

