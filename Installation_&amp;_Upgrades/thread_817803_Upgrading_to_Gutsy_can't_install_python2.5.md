---
title: "Upgrading to Gutsy: can't install python2.5"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by Tacit Orange on 2008-06-04
Well, it's been a long couple of days of troubleshooting on my own, trying to get my old Edgy installation up to date (dealing with the "discontinued support" in the form of deleted software repositories was a real blast -- real slick move there in this age of nearly free drive space). I've managed to get as far as running the graphical update tool to upgrade to Gutsy, but there have been a couple of hiccups which have led to gnome and a couple of other *really important* packages getting broken. Following advice I've found here through forum searches, I ran
```
sudo dpkg --configure -a
```
to try and sort things out and got a slew of error messages. I've tracked the problem down to a failure to install the python2.5 package. Here's what happened when I tried to install it by itself:
```
me@mymachine:~$ sudo dpkg --configure python2.5
Setting up python2.5 (2.5.1-5ubuntu5.1) ...

(update-desktop-database:6115):Glib-CRITICAL**: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing python2.5 (--configure):
 subprocess post-installation script returned error exit status 139
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python2.5
me@mymachine:~$ 
```
What is going on here and how do I fix it? I hope I get at least one reply for my efforts; I had to boot into failsafe xterm and scribble the error message down on a pad of paper to post on this forum using my laptop :(

---

### Post by Tacit Orange on 2008-06-04
Anyone?

---

### Post by bapoumba on 2008-06-04
Please post your sources.list:
```
cat /etc:apt/sources.list
```

As a side note, old releases repos are [there]("http://old-releases.ubuntu.com/releases/"), and not maintained any longer. I just discovered getting to the url that dapper repos are also there.

---

### Post by Tacit Orange on 2008-06-04
Here are the contents of /etc/apt/sources.list (commented lines deleted for brevity):
```
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

---

### Post by Tacit Orange on 2008-06-05
Anybody know what's going on?

---

### Post by zvacet on 2008-06-05
Your source list is not complete.Try with this one 

>  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

```
sudo apt-get update && sudo apt-get upgrade
```

---

