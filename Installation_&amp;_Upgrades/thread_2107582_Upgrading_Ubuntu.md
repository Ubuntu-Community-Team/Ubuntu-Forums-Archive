---
title: "Upgrading Ubuntu"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by jbcohen on 2013-01-22
When I set about upgrade my installation of ubuntu to the latest versions every month or so what is the preferred method t accomplish this: downloading a new version from the ubuntu web site or perhaps using the update function from within ubuntu?

---

### Post by omeomi on 2013-01-22
Do you mean upgrade the distribution or just the latest versions of packages? In the first case, this only happens twice a year not every month. 

In both cases the easiest way is to use the Software Update in Ubuntu. By default it will tell you when new updates (including new distributions) are available for download.

---

### Post by Bucky Ball on 2013-01-22
There is no latest version every month or so. A new release comes out every six months. 12.04 LTS is the current long-term support release and I would advise keeping that or a least a stable release on one partitions and installing the new releases on another as they will not necessarily be stable and you can expect breakages and bugs, especially within the first few months.

The next release is 13.04 in April of this year.

If you are just talking about upgrading the apps and other things in your installation and not the entire release, run these to commands in a terminal, _*always*_ in this order:

```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ibjsb4 on 2013-01-22
Here's some more info.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_13.04_.28Raring_Ringtail.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_13.04_.28Raring_Ringtail.29)

---

### Post by jbcohen on 2013-01-22
I'm used to Microsoft Windows that seems to patch their software a few times each day, then put out Service Packs which are sort of earth shattering.  I 'm still getting use to Ubuntu's way of doing things.  The Ubuntu web site talks about version 12.1 and you all are talking about what seems to be an older version, how can 12.04 be the latest when the web site talks about 12.1.

I am a little maniac about keeping my software up to date because some time ago I had major problems on windows 7 because I did not have service one and I couldn't get Microsoft to let me have the service pack.  so I developed a bit of an upgrade obsession there which has carried over here.  I guess I will use the package updater to keep me on top of things, I see the switches in the software to allow the updater to do all of its work without asking me, and that's what I want.

I think perhaps 12.04 is the latest stable version and 12.1 is the latest unstable one?  Anyhow I think that I should rely on the updater to keep me on top of the latest packages.  There's that term packages, I am going to need to get used to that term, I am a very new transplant from a windows environment so as a consequence my terms are still Windows.  In windows we call them upgrades or updates, upgrades are a big headache and cost $$$, updates don't and are incremental fixes in the software.  Ubuntu seems to use the term packages for both.

---

### Post by Frogs Hair on 2013-01-22
In update manager > settings you choose different update options. Mine may look different on 12.10 and I also update daily but that is up to you.

---

### Post by grahammechanical on 2013-01-22
Ubuntu has a 25 week development schedule. It is never the intention of the developers to release an unstable version of Ubuntu. But it is not always possible to get everything correct in the time allowed. This is why some of us recommend waiting a few weeks after the release date before upgrading or fresh installing.

Having said that I am using Ubuntu Raring Ringtail (13.04) right now. I have been using it every day since development first started on it. It, in my opinion, is stable enough to do daily work. Just do not keep your data and files on the same partition as a development branch version. You never know when you may need to do a re-install. And always have another version of Ubuntu as a standby OS.

Ubuntu has support for security fixes for 18 months. Then every two years a version is released that has support for more than 18 months. Those versions are called Long Term Support (LTS).

Ubuntu 12.04 has support for 5 years. Ubuntu 12.10 has support for 18 months. And so will 13.04 and 13.10. Then 14.04 will get 5 years support. This is how the Ubuntu community developers take care of us.

I think that you are confusing Upgrades with Updates. Go to System Settings>Software Sources and open the Updates tab. There you can set the time interval for being notified of any updates.

Daily; Every two days; Weekly; Every Fortnight; never.

You can set security updates for

Display immediately; Download automatically; Download and install automatically.

As for Upgrades you can set

For any new version; For Long Term support Versions; Never.

In my opinion, if the system has not been heavily modified by you, and if you are upgrading from one version of Ubuntu to the next, then Upgrading is not so risky. But,

If the system has been heavily modified then it is too much to expect the Upgrade process to make all the changes without messing things up. also,

If you are going from very old releases to the latest release then expect problems. A new install is better in these situations. Again, this is my opinion.

Regards.

---

### Post by omeomi on 2013-01-22
> **jbcohen said:**
> I think perhaps 12.04 is the latest stable version and 12.1 is the latest unstable one? 

This is more or less correct. For stability you do want to stay at 12.04 which is the current Long Term Support (LTS) version. If you want the latest stuff you need to use the most recent version which currently is 12.10.

When a new distribution arrives (the next will be 13.04 in april) you can just upgrade from the Software Updater without much effort. 

This is all a lot easier than it was in Windows and you will get used to soon enough!

---

### Post by jbcohen on 2013-01-22
I see in what omeomi has to say the easiest way to stay upto date is using the updater  that comes with  the software.  When version 2.1 becomes stable will the updater install the new est version for me or will I need to download and install that from the web site?  I like to have a CD of what ever version I have on hand in case something crashes so I can re-install, I can cut a DVD or I can order for a small fee a DVD of the version from what web site?

---

### Post by Cheesemill on 2013-01-22
Ubuntu versions that aren't LTS are not 'non-stable'.

All released versions of Ubuntu are stable, the only difference between a normal release and an LTS release is the amount of time they are supported for (18 months vs. 5 years).

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

You have to weigh up the pros and cons of each to make an informed decision as to which is right for you. Either stay with LTS releases which are supported for longer but don't have the latest versions of software, or upgrade to each normal release every 6 months and have the latest versions of software.

---

### Post by Bucky Ball on 2013-01-22
The current 12.04 is 12.04.1. There seems to be some confusion between this and 12.10, a totally different release.

---

