---
title: "Fennec 1.0a1 - The Mobile Firefox"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubulette on 2008-10-17
I just updated my package for Fennec, the Mobile version of Firefox from Mozilla, to [1.0 Alpha 1]("http://starkravingfinkle.org/blog/2008/10/fennec-m9-user-experience-alpha/"). It is designed for Internet Tablets, but could also be used on Desktops. If you want to feel the mobile experience, read the rest :cool:

As xulrunner-1.9.1 (and then firefox 3.1) didn't make it into Intrepid, Fennec could not be shipped either so it's living in my PPA as a preview package until it enters the official repository, hopefully in Jaunty.

I provide Fennec for both Hardy and Intrepid (you will need my xulrunner-1.9.1 too).
Please see [https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)
Feedbacks appreciated.

---

### Post by jfernyhough on 2008-10-17
Nice. I just saw the release on Slashdot and grabbed the version from the Mozilla FTP.

It looks promising - especially for small screen UMPCs like the EeePC. It has a few rough edges still, like the version I have won't do right-clicks, but for an alpha it's pretty darned good.

---

### Post by Jay_Bee on 2008-10-17
Can't be installed in Hardy:
```
xulrunner-1.9.1:
  Depends: libasound2 (>1.0.17), but 1.0.15-3ubuntu4 will be installed
  Depends: libgtk2.0-0 (>=2.14.1), but 2.12.9-3ubuntu5 will be installed
 Depends: libhunspell-1.2-0 (>=1.2.4) but it is not installable
  Depends: libpango1.0-0 (>=1.21.6), but 1.20.5-0ubuntu1 will be installed
```

---

### Post by ubulette on 2008-10-17
> **Jay_Bee said:**
> Can't be installed in Hardy:
```
xulrunner-1.9.1:
  Depends: libasound2 (>1.0.17), but 1.0.15-3ubuntu4 will be installed
  Depends: libgtk2.0-0 (>=2.14.1), but 2.12.9-3ubuntu5 will be installed
 Depends: libhunspell-1.2-0 (>=1.2.4) but it is not installable
  Depends: libpango1.0-0 (>=1.21.6), but 1.20.5-0ubuntu1 will be installed
```

You are not using the right package.
All my debs are taggued, ~ftaX for intrepid, and ~ftaX~hardy for hardy.

Here is the install on hardy:

```

The following NEW packages will be installed:
  fennec
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 500kB of archives.
After this operation, 930kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  fennec
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net hardy/main fennec 1.0~a1-0ubuntu1~fta1~hardy [500kB]
Fetched 500kB in 0s (3822kB/s)
Selecting previously deselected package fennec.
(Reading database ... 278724 files and directories currently installed.)
Unpacking fennec (from .../fennec_1.0~a1-0ubuntu1~fta1~hardy_i386.deb) ...
Setting up fennec (1.0~a1-0ubuntu1~fta1~hardy) ...
$ apt-cache madison libasound2
libasound2 | 1.0.15-3ubuntu4 | http://archive.ubuntu.com hardy/main Packages
  alsa-lib | 1.0.15-3ubuntu4 | http://archive.ubuntu.com hardy/main Sources

```

---

### Post by Jay_Bee on 2008-10-17
You are right, I was trying to install from the intrepid repo. It's working now.
I noticed that the top "url bar" doesn't always hide when I scroll down, is that expected behaviour?

---

### Post by jfernyhough on 2008-10-17
j@t7200:~$ fennec 
Could not read application.ini

Hmm... am I missing something? I installed Fennec and XULRunner 1.9.1.

---

### Post by ubulette on 2008-10-17
> **jfernyhough said:**
> j@t7200:~$ fennec 
Could not read application.ini

Hmm... am I missing something? I installed Fennec and XULRunner 1.9.1.

strange. It means the stub has lost its libdir.
Did you run it at least once before you installed xul 1.9.1 ?

try to move away ~/.mozilla/fennec/
If it still doesn't work, try to run it from /usr/lib/fennec-*/fennec
If only the last option works, I may have to add a launcher script like I did for firefox..

---

### Post by inportb on 2008-10-17
Ooh, nifty. I just installed fennec and think it's awesome for an alpha release. Right-click in a touchscreen environment obviously doesn't make much sense, and drag-navigation is obviously not the most comfortable action to perform using a mouse. But hey, it's great for compatibility-testing.

Thanks ubulette ;p

---

### Post by klange on 2008-10-17
> **inportb said:**
> Ooh, nifty. I just installed fennec and think it's awesome for an alpha release. Right-click in a touchscreen environment obviously doesn't make much sense, and drag-navigation is obviously not the most comfortable action to perform using a mouse. But hey, it's great for compatibility-testing.

Thanks ubulette ;p

Right clicking on a touchscreen was actually perfected years ago - you click and hold in the typical set up. I guess a touchpad or tablet would be better suited for testing the drag navigation.

---

### Post by inportb on 2008-10-18
> **WindowsSucks said:**
> Right clicking on a touchscreen was actually perfected years ago - you click and hold in the typical set up. I guess a touchpad or tablet would be better suited for testing the drag navigation.

Well that's still click-and-hold in mouse terminology, not right-click ;p

---

### Post by jfernyhough on 2008-10-18
> **ubulette said:**
> strange. It means the stub has lost its libdir.
Did you run it at least once before you installed xul 1.9.1 ?I ran the version from the Mozilla FTP before I installed your Fennec and XUL, but I didn't run your Fennec seperately.> try to move away ~/.mozilla/fennec/Already done. :)
> If it still doesn't work, try to run it from /usr/lib/fennec-*/fennecThat works.

I'll try a purge and reinstall to see if that makes any difference, seeing as it works for other people as expected.

--edit
OK, no difference. Running 'fennec' give the same error. However, running /usr/bin/fennec works fine.

---

### Post by Jay_Bee on 2008-10-19
I like it.
It's missing the ability to scroll the url-bar suggestions.
Will it be possible to use on non-touchscreen mobile phones?

---

### Post by sethvath on 2008-10-19
You need to click and drag (left and right) to access the controls. My guess is no it wont work fully on non-touchscreen mobile phones without any modifications.

---

