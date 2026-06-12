---
title: "Firefox would NOT upgrade to version 3.5.3"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rykel on 2009-10-11
Hi all,

I am using Karmic, but no matter how often I upgrade, Firefox stays at version 3.5.2 and would NOT upgrade to 3.5.3.

Can you please help me?

Thanks!

---

### Post by dentaku65 on 2009-10-11
> **rykel said:**
> Hi all,

I am using Karmic, but no matter how often I upgrade, Firefox stays at version 3.5.2 and would NOT upgrade to 3.5.3.

Can you please help me?

Thanks!

Can you try to upgrade with
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
and post here the output?

---

### Post by rykel on 2009-10-11
Sure!

As you can see, there does not seem to be any problem.


> $ sudo apt-get update
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/main Translation-en_SG                 
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/universe Translation-en_SG             
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/restricted Translation-en_SG 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                  
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/multiverse Translation-en_SG 
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-security Release.gpg         
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_SG    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                      
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/main Translation-en_SG
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/universe Translation-en_SG
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/restricted Translation-en_SG
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/multiverse Translation-en_SG
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic Release
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-security Release            
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates Release             
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/main Packages               
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/universe Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_SG
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/main Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_SG
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/restricted Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-security/main Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-security/universe Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_SG
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_SG
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Reading package lists... Done

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



---

### Post by slakkie on 2009-10-11
What does apt-cache policy firefox say?

---

### Post by rykel on 2009-10-11
It says...

> $ apt-cache policy firefox
firefox:
  Installed: 3.5.3+build1+nobinonly-0ubuntu3
  Candidate: 3.5.3+build1+nobinonly-0ubuntu3
  Version table:
 *** 3.5.3+build1+nobinonly-0ubuntu3 0
        500 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status


---

### Post by dentaku65 on 2009-10-11
mmm...
what about to do
```
sudo apt-get remove firefox && sudo apt-get install firefox
```

---

### Post by aysiu on 2009-10-11
Can you paste these commands into the terminal and post the output back here?```
ls /opt
ls -l /usr/bin/firefox
dpkg -s firefox
dpkg -s firefox-3.5
cat /etc/lsb-release
uname -a
```

---

### Post by slakkie on 2009-10-11
> **rykel said:**
> It says...

Well, you are running firefox 3.5.3..

---

### Post by rex4u on 2009-10-11
Try this
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

A bit off-topic but I would suggest you try Opera 10 also.

---

### Post by rykel on 2009-10-11
> **aysiu said:**
> Can you paste these commands into the terminal and post the output back here?```
ls /opt
ls -l /usr/bin/firefox
dpkg -s firefox
dpkg -s firefox-3.5
cat /etc/lsb-release
uname -a
```

The result is:
> 
$ ls /opt
firefox  google

$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2009-08-11 03:53 /usr/bin/firefox -> /opt/firefox/firefox

$ dpkg -s firefox
Package: firefox
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 128
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: all
Source: firefox-3.5
Version: 3.5.3+build1+nobinonly-0ubuntu3
Depends: firefox-3.5, firefox-3.5-branding
Description: meta package for the popular mozilla web browser
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
 .
 This is a meta package that will point to the latest firefox package in ubuntu.
 Don't remove this if you want to receive automatic major version upgrades for
 this package in future.

$ dpkg -s firefox-3.5
Package: firefox-3.5
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 3676
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.5.3+build1+nobinonly-0ubuntu3
Replaces: firefox-3.0, firefox-3.1
Provides: firefox-3.1, www-browser
Depends: fontconfig, psmisc, debianutils (>= 1.16), xulrunner-1.9.1 (>= 1.9.1), libasound2 (>> 1.0.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.10), libnspr4-0d (>= 4.7.3-0ubuntu1~), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.1.1), firefox-3.5-branding | abrowser-3.5-branding
Recommends: ubufox
Suggests: firefox-3.5-gnome-support (= 3.5.3+build1+nobinonly-0ubuntu3), latex-xft-fonts, libthai0
Conflicts: firefox-3.1 (<< 3.1~b4~hg20090317)
Conffiles:
 /etc/apparmor.d/usr.bin.firefox-3.5 59da8c65b5edc154cd6818036a69243e
 /etc/firefox-3.5/profile/bookmarks.html 111416629615cf48b389d1c5d5c11c27
 /etc/firefox-3.5/profile/localstore.rdf ea03cc19c2a3f622fa557cd8ea9da6eb
 /etc/firefox-3.5/profile/prefs.js 99940ecd258d83b3355ab06fca0ffddb
 /etc/firefox-3.5/profile/mimeTypes.rdf 6047f42624d9930caa8d651fa94d28f1
 /etc/firefox-3.5/profile/chrome/userChrome-example.css c63733eef9d337c86e6609bcc478a668
 /etc/firefox-3.5/profile/chrome/userContent-example.css d3765c7d2de5626529195007f4b7144a
 /etc/firefox-3.5/pref/firefox.js ef558140ade20eabae7075894cc98398
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"

$ uname -a
Linux SuperStar 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 i686 GNU/Linux

As you can see, it looks like 3.5.3 but in the "Help/About Mozilla Firefox" tab it says 3.5.2, and I know it IS 3.5.2 because Flash fullscreen crashes it!    :)

Please help!

---

### Post by aysiu on 2009-10-12
The problem is you installed the Mozilla binary and put it in /opt and symlinked it to /usr/bin/firefox

That Firefox is 3.5.2

The Firefox from the Ubuntu repositories is 3.5.3.

So which do you want to use? If you let me know, I'll let you know what appropriate action to take to use 3.5.3.

---

### Post by rykel on 2009-10-12
Oh I see.. I want to use 3.5.3 from Ubuntu, definitely!

Thanks for your help, aysius!!

---

### Post by aysiu on 2009-10-12
This will help you, then:
[http://psychocats.net/ubuntu/firefox#remove](http://psychocats.net/ubuntu/firefox#remove)

---

### Post by rykel on 2009-10-12
hi aysius,

thanks man i think ur solution will work... however, before i attempt to remove my current firefox using ur method, how do i ensure that my current settings and profiles will NOT be deleted as well?

can i back them up somewhere?

---

### Post by cariboo on 2009-10-12
In a standard installation of Firefox your profile is located in your home directory. it is located in ~/.mozilla. In nautilus press Ctrl-h to reveal hidden files and directories.

---

### Post by aysiu on 2009-10-12
> **rykel said:**
> hi aysius,

thanks man i think ur solution will work... however, before i attempt to remove my current firefox using ur method, how do i ensure that my current settings and profiles will NOT be deleted as well?

can i back them up somewhere?
Close Firefox.

Then make a copy of the /home/rykel/.mozilla folder (it is a hidden folder).

Then follow those instructions to remove the /opt Firefox. The removal should not affect your settings, but you're right--it is a good idea to back that stuff up anyway.

---

### Post by rykel on 2009-10-12
Hi all,

Just want to gladly tell everybody that Aysius' instructions worked!

And they did NOT delete away any profile or setting.

Thank you!!

---

