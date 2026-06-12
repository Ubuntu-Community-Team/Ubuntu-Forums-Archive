---
title: "Cannot  add any software using app-&gt;add or apt-get"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by sonyisme on 2008-01-23
I use applications-> add/remove...
whatever I tick to install, it tells me that "The list of the applications is not available, press reload to refresh it". Then the same thing happens.

I checked system updates, and the system is up2date.

I also tried sudo apt-get install sun-j2re1.5, it doesn't work.
Actually whatever package I want to install, it fails with the
same info.

sonyisme@sonyisme:~$ sudo apt-get install sun-j2re1.5
[sudo] password for sonyisme:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-j2re1.5

---

### Post by jon_gunnar on 2008-01-23
> **sonyisme said:**
> I use applications-> add/remove...
whatever I tick to install, it tells me that "The list of the applications is not available, press reload to refresh it". Then the same thing happens.

I checked system updates, and the system is up2date.

I also tried sudo apt-get install sun-j2re1.5, it doesn't work.
Actually whatever package I want to install, it fails with the
same info.

sonyisme@sonyisme:~$ sudo apt-get install sun-j2re1.5
[sudo] password for sonyisme:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-j2re1.5

Actually I cant find this package on my system either.But a search like this:
```
jon@jon-desktop:~$ apt-cache search sun
```
Brings up a lot of hits for Sun java,amongs them just as an example is  sun-java6-jre
```
jon@jon-desktop:~$ apt-cache show sun-java6-jre
Package: sun-java6-jre
Priority: optional
Section: multiverse/libs
```

As you can see this is to be found in multiverse.Have a look at you're sources file and see what you got.As an example here is mine:

```
jon@jon-desktop:~$ cat /etc/apt/sources.list

deb http://ftp.uninett.no/ubuntu/ gutsy main restricted
deb-src http://ftp.uninett.no/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.uninett.no/ubuntu/ gutsy-updates main restricted
deb-src http://ftp.uninett.no/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ftp.uninett.no/ubuntu/ gutsy universe
deb-src http://ftp.uninett.no/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.uninett.no/ubuntu/ gutsy multiverse
deb-src http://ftp.uninett.no/ubuntu/ gutsy multiverse

deb http://ftp.uninett.no/ubuntu/ gutsy-security main restricted
deb-src http://ftp.uninett.no/ubuntu/ gutsy-security main restricted
deb http://ftp.uninett.no/ubuntu/ gutsy-security universe
deb-src http://ftp.uninett.no/ubuntu/ gutsy-security universe
deb http://ftp.uninett.no/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://ftp.uninett.no/ubuntu/ gutsy-backports restricted main multiverse universe
deb-src http://ftp.uninett.no/ubuntu/ gutsy-security multiverse
```

If all this is things you have done already Im not sure what the problem is.

---

### Post by Kevbert on 2008-01-23
It looks like you haven't got all the important software sources activated.   Go to System - Administration - Software Sources.  Under the Ubuntu Software tab check at least the first two boxes.

---

### Post by sonyisme on 2008-01-23
> **Kevbert said:**
> It looks like you haven't got all the important software sources activated.   Go to System - Administration - Software Sources.  Under the Ubuntu Software tab check at least the first two boxes.
It doesn't work for me. Apparently none of the boxes were checked. But when I tried to check the
first two. It tells me that the connection to those two sites failed.
(main) and (universe).

---

### Post by zvacet on 2008-01-24
Select main server and try again.You must be able to open repositories.It is basic.Maybe some server thing,but youi have to open them(repos)if you want to get all packages.

---

### Post by Kevbert on 2008-01-24
> **sonyisme said:**
> It doesn't work for me. Apparently none of the boxes were checked. But when I tried to check the
first two. It tells me that the connection to those two sites failed.
(main) and (universe).

How are you connected to the internet ?  You need to be connected to the Web.  Also, in the 'Download from;' box under Software Sources - Ubuntu Software select either Main or Other.  In the case of 'Other' click on 'Select Best Server'.  Under the Software Sources Updates tab make sure that 'Important' and 'Recommended' update boxes are selected.  Next go to System - Administration - Update Manager and check for updates - you'll probably have a few.
If this does not work you may have an internet connection problem.

---

