---
title: "Will the 64 bit ubuntu restricted extras have Java 64 included?"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hotweiss on 2009-04-03
Will the 64 bit Ubuntu restricted extras have Java 64 included?

---

### Post by hotweiss on 2009-04-05
bump

---

### Post by diebels on 2009-04-05
It has jre included in recommends, as plugin it has icedtea6-plugin. So you'll have to install sun-java6-plugin explicitly to get the web-browser-plugin.

---

### Post by Koraq on 2009-04-07
Where do you find those?

None of:

icedtea6-plugin
sun-java6-plugin

show up when I run apt-cache search

---

### Post by ormandj on 2009-04-07
> **Koraq said:**
> Where do you find those?

None of:

icedtea6-plugin
sun-java6-plugin

show up when I run apt-cache search

Do you have Multiverse enabled?

ormandj@ormandj-laptop:~$ sudo apt-cache show sun-java6-plugin
Package: sun-java6-plugin
Priority: optional
Section: multiverse/web
Installed-Size: 100
Maintainer: Matthias Klose <doko@ubuntu.com>
Architecture: amd64
Source: sun-java6
Version: 6-13-1
Depends: libasound2, libx11-6, libxext6, libxi6, libxt6, libxtst6, sun-java6-bin (= 6-13-1), firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | xulrunner
Filename: pool/multiverse/s/sun-java6/sun-java6-plugin_6-13-1_amd64.deb
Size: 1960
MD5sum: ed83d423210b94079cd59947c27acc90
SHA1: 107944fba0416bd5a009cc27be9ca3a14d98dbe6
SHA256: 4fe59d357ed105d9883d7a18424e2191ade2fd693ddeb25543f25ba84ad5e886
Description: The Java(TM) Plug-in, Java SE 6
 Java Plug-in enables applets written to the Java Platform 6
 specification to be run in Mozilla and other web browsers.
 Java Plug-in comes with the Java Runtime Environment (JRE).
 .
 This is a metapackage containing dependencies for running Java in
 various browsers.
Homepage: [http://java.sun.com/javase/](http://java.sun.com/javase/)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Mimetype: application/x-java-vm, application/x-java-applet, application/x-java-applet;version=1.1, application/x-java-applet;version=1.1.1, application/x-java-applet;version=1.1.2, application/x-java-applet;version=1.1.3, application/x-java-applet;version=1.2, application/x-java-applet;version=1.2.1, application/x-java-applet;version=1.2.2, application/x-java-applet;version=1.3, application/x-java-applet;version=1.3.1, application/x-java-applet;version=1.4, application/x-java-applet;version=1.4.1, application/x-java-applet;version=1.4.2, application/x-java-applet;version=1.5, application/x-java-applet;version=1.6, application/x-java-applet;jpi-version=1.6.0_07, application/x-java-bean, application/x-java-bean;version=1.1, application/x-java-bean;version=1.1.1, application/x-java-bean;version=1.1.2, application/x-java-bean;version=1.1.3, application/x-java-bean;version=1.2, application/x-java-bean;version=1.2.1, application/x-java-bean;version=1.2.2, application/x-java-bean;version=1.3, application/x-java-bean;version=1.3.1, application/x-java-bean;version=1.4, application/x-java-bean;version=1.4.1, application/x-java-bean;version=1.4.2, application/x-java-bean;version=1.5, application/x-java-bean;version=1.6, application/x-java-bean;jpi-version=1.6.0_07
Npp-Name: The Java(TM) Plug-in, Java SE 6
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

ormandj@ormandj-laptop:~$

---

### Post by Koraq on 2009-04-08
Looks like it:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse


deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security multiverse


deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted

---

### Post by taavikko on 2009-04-08
@korag, you're running hardy?
64bit browser-plugin isn't in 8.04.

---

### Post by Koraq on 2009-04-08
I don't know, but it does say hardy in sources.list so I guess, yes I am.

So if this package is not in 8.04, how do I upgrade?

---

### Post by miklcct on 2009-04-09
The package is in 9.04. If you want to upgrade your whole system, you may upgrade to 8.10 first and to 9.04

---

### Post by diebels on 2009-04-09
Koraq,
you can run update manager with the -c switch.
```
update-manager -c
```
This will get you up to 8.10.

If you want upgrade to 9.04 before it is released, you need the -d switch.
```
update-manager -d -c
```
You may see somebody saying just replace hardy with intrepid and jaunty in sources lits, and use apt-get to upgrade.

Don't do this, as it does not get around quircks in the upgrade process as well as update-manger.

---

### Post by Koraq on 2009-04-09
I ran do-release-upgrade since I didn't find any update-manager. Now I seems to be running a newer release. Thanks.

But I still don't see that package: sun-java6-plugin

---

### Post by taavikko on 2009-04-10
Let's make sure your running Jaunty
```
lsb_release -rd; uname -r
```

---

### Post by Polygon on 2009-04-10
a dist upgrade would of upgraded him to intrepid, right? unless he forced it to look for beta releases

---

### Post by ubuntu27 on 2009-04-10
Koraq. I recommend you to do a Clean/Fresh Install (not upgrade, but to install new Ubuntu over the old version) of Ubuntu Jaunty.

Ubuntu Jaunty will be released on [April 23]("https://wiki.ubuntu.com/JauntyReleaseSchedule").

You can wait until it is officially released or jump in the current Beta or wait for the RC (Release Candidate). 

It is better to wait for stability thou.

The new version of Ubuntu has more 64-bit apps including Java 64-bit.

---

### Post by Koraq on 2009-04-13
Description:    Ubuntu 8.10
Release:        8.10
2.6.27-11-server
lad@Upheaval:~$

Is my state now. That isn't Jaunty, is it? I do have KDE4.2 now, though. 

Yeah, maybe I should just wait. And frankly, I'm beginning to think the web training that I needed java for just isn't worth it.

Thanks a lot for your patience guys.

---

