---
title: "Possible to have ubuntu 16.04 version updated to wine release?"
date: 2017-10-06
forum: MINT
---

### Post by tgp1994 on 2017-10-06
I'm on mint 18.02 which is apparently based on ubuntu 16.04. The version of wine for me is ```
wine-1.6.2
```, which I think is quite a ways behind the version at [winehq]("https://www.winehq.org/announce/2.0.2") stable which as of now is ```
2.0.2
```. I'd like to help with this if that's ok but I'm totally new to this, do I need to file a bug report?

---

### Post by mikewhatever on 2017-10-06
Here you go: [http://www.omgubuntu.co.uk/2017/04/how-to-add-wine-repository-ubuntu](http://www.omgubuntu.co.uk/2017/04/how-to-add-wine-repository-ubuntu).

---

### Post by ajgreeny on 2017-10-06
Thread moved to Mint.

---

### Post by tgp1994 on 2017-10-06
> **mikewhatever said:**
> Here you go: [http://www.omgubuntu.co.uk/2017/04/how-to-add-wine-repository-ubuntu](http://www.omgubuntu.co.uk/2017/04/how-to-add-wine-repository-ubuntu).

Thank you for the link Mike. I'm already familiar with the official Wine repository, in fact that's where I got the stable version number (2.0.2) from. I'll probably end up using this anyways, but I just wanted to benefit the Ubuntu community by having their repository updated too. I mean, why does Ubuntu keep Wine available if it doesn't want to update it?

> **ajgreeny said:**
> Thread moved to Mint.

With all due respect, [I don't think this is a mint issue]("https://ubuntuforums.org/showthread.php?t=2059684"). I believe this is more related to the wine package in the Ubuntu repositories, hence why I posted in the Wine subforum.

---

### Post by ian-weisser on 2017-10-06
> **tgp1994 said:**
> I just wanted to benefit the Ubuntu community by having their repository updated too. I mean, why does Ubuntu keep Wine available if it doesn't want to update it?

Newer releases of Ubuntu have newer versions of Wine. Older releases of Ubuntu have correspondingly older versions of Wine.

 Ubuntu is a *snapshot distro*, not a *rolling distro*.
A 'snapshot distro' has a single frozen set of applications that depend upon identical versions of all dependencies. This prevent all kinds of dependency problems. Ubuntu takes a new snapshot every six months, and spends several months ironing out all the bugs and incompatibilities so you don't have to.
With only a few exceptions (security, major bugs, backports), none of the software gets updated after release. There are some very good historical reasons for this.

If you want newer versions of software, you get it every six months when the next release of Ubuntu becomes available.
...unless, of course, you use an LTS release. LTS releases achieve their reputation for stability by keeping most software frozen for five years. Not for people who want new stuff.

You can also use Snaps, Flatpacks, AppImages, and other non-debian packages to add newer software to an Ubuntu system. They have their own sets of advantages and disadvantages.

---

### Post by tgp1994 on 2017-10-06
> **ian-weisser said:**
> Newer releases of Ubuntu have newer versions of Wine. Older releases of Ubuntu have correspondingly older versions of Wine.

 Ubuntu is a *snapshot distro*, not a *rolling distro*.
A 'snapshot distro' has a single frozen set of applications that depend upon identical versions of all dependencies. This prevent all kinds of dependency problems. Ubuntu takes a new snapshot every six months, and spends several months ironing out all the bugs and incompatibilities so you don't have to.
With only a few exceptions (security, major bugs, backports), none of the software gets updated after release. There are some very good historical reasons for this.

If you want newer versions of software, you get it every six months when the next release of Ubuntu becomes available.
...unless, of course, you use an LTS release. LTS releases achieve their reputation for stability by keeping most software frozen for five years. Not for people who want new stuff.

You can also use Snaps, Flatpacks, AppImages, and other non-debian packages to add newer software to an Ubuntu system. They have their own sets of advantages and disadvantages.

Yup, I think I understand how Ubuntu releases work. I'd just like to do a little math though;

So I'm having trouble finding out exactly when Wine released 1.6.2, the version that's also currently offered for Ubuntu Xenial 16.04. For the sake of argument then, lets look at [1.7.0, released August 2nd, 2013]("https://www.winehq.org/news/2013080202"). Looking at the [Ubuntu releases]("https://wiki.ubuntu.com/Releases") page, 16.04 was originally released on April 21, 2016. If I'm understanding this correctly, by the time Ubuntu 16.04 was released, Wine was already nearly *three years old*! I get that an LTS is meant to be super stable, but I thought that meant keeping the software stable for five years, not using very old software right when it goes to release. You say that the goal is to prevent headaches by keeping out bugs, yet here I find myself on the Ubuntu forums debating with the community about software release cycles, all because I'm dealing with a bug that's years old! :p

Looking at the [Launchpad packages page]("https://launchpad.net/wine/+packages") in Ubuntu's packages site now, even 17.04 Zesty is using Wine version 1.8.4 in its primary package source (again if I'm interpreting this correctly). However, I think I do see 2.0.2 gradually making its way through some unstable repos.

Look, I definitely don't want to argue about Ubuntu's package policies and what not. It's not that big of a deal to me, and at the end of the day I'll just find another way to get the latest version and go my way. I just wanted to understand why the Ubuntu repos appeared to be so far behind, if it was just a policy or if it might have been forgotten. Again if there's any help needed here I think could contribute.

---

### Post by ian-weisser on 2017-10-06
> **tgp1994 said:**
> Look, I definitely don't want to argue about Ubuntu's package policies and what not. It's not that big of a deal to me, and at the end of the day I'll just find another way to get the latest version and go my way. I just wanted to understand why the Ubuntu repos appeared to be so far behind, if it was just a policy or if it might have been forgotten. Again if there's any help needed to here I think could contribute.

That's a wise way to look at it.
As far as Ubuntu is concerned, it's pretty simple: If a volunteer in Debian packages it, and it lacks critical bugs, then Ubuntu will merge it into the next release automagically.
If I recall correctly, there were a few years of rather annoying Wine bugs, and a bit of turbulence among Debian maintainers, that prevented the version of Wine being updated in Ubuntu.
Quite a few people were annoyed (and complained here), but few --if any-- got involved enough to solve the problem.

---

### Post by tgp1994 on 2017-10-06
> **ian-weisser said:**
> That's a wise way to look at it.
As far as Ubuntu is concerned, it's pretty simple: If a volunteer in Debian packages it, and it lacks critical bugs, then Ubuntu will merge it into the next release automagically.
If I recall correctly, there were a few years of rather annoying Wine bugs, and a bit of turbulence among Debian maintainers, that prevented the version of Wine being updated in Ubuntu.
Quite a few people were annoyed (and complained here), but few --if any-- got involved enough to solve the problem.

Alright, maybe I can still do something positive here. I'll go over to the debian area and see what's up over there. Thank you!

---

### Post by qyot27 on 2017-10-06
Wine also changed their versioning methods, with 1.odd being devel releases, 1.even being the stable ones, and a tendency toward a 'when it's ready' attitude toward closing off the devel branch and launching a new stable series.  I seem to remember the 1.7 devel branch stayed around for a super long time and since Debian and Ubuntu would rely on Wine-stable, it likewise took forever to move from stable series 1.6 to stable series 1.8.

I seem to remember reading that with Wine 2.x, that versioning methodology changed to facilitate more rapid development cycles.  But I could be wrong.

---

### Post by tgp1994 on 2017-10-06
I think you're correct; I was reading the news to get a better idea of how many features and bugfixes I was missing out on (lol) and it looks like since version 2, they switched to an annual release cycle. All the same though, the current version(s) of wine in the Ubuntu repos are *just plain old*.

---

### Post by qyot27 on 2017-10-06
According to the news roll on winehq, 1.8 was released in December 2015.

Which version of a package is determined by the Ubuntu Release Schedule.  [This is the one for Xenial](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule).  Some pieces of software (the Linux kernel, mainly) get special milestone treatment apart from usual software (like Wine).  After the [Debian Import Freeze](https://wiki.ubuntu.com/DebianImportFreeze), software packages don't get newer* versions unless specifically requested.

*newer in this case referring to a release branch.  Bugfix releases in the same branch would obviously be allowed insofar as you also get those for normal Ubuntu releases, although said bugfix releases might be delayed until after the official release in April or October.

So there was indeed a breakdown of sorts in the early part of 2016 that led to 16.04 shipping with the old 1.6 stable branch of Wine, despite 1.8 stable having been released basically two months to the day prior to the Debian Import Freeze occurring.  As someone mentioned above, if the Wine package maintainers in Debian and/or Ubuntu were having issues with either administrative tasks in getting the 1.8 package into the repositories on time, or that the 1.8 package had issues requiring it be delayed, that could cause it.  Wine 1.7 was not eligible for inclusion because it was a -devel branch.  Wine 1.8 was included in Yakkety/16.10, Wine 1.9 was not eligible for inclusion because it was -devel, Wine 2.0 was released on 2017-01-24, which was even closer to the Import Freeze for Zesty than 1.8 was (so if the same situation occurred, it'd be delayed even further past the Freeze).  However, the wine package in Ubuntu - maybe in Debian as well - has changed into a virtual package used by the packages wine-stable and wine-development.  I think I remember this changing in Yakkety, but since those repos have been removed, we can only look at Zesty's, where wine-stable in 1.8 and wine-development is 2.0.

And of course that's where the difference is.  Referring to 'wine' all by itself is shorthand for wine-stable for most people, and that's why I pointed out 1.7 and 1.9 weren't included.  wine-development is always a little newer, though, and Xenial's wine-development version is 1.9.6, and it did manage to get in before the Import Freeze, since 1.9 was released on 2015-12-25 (1.9.6 on 2016-03-18).  It certainly is true that an up-to-date bugfix release of 1.9 could probably be added, since 1.9.24 was released on 2016-11-25, but the wine-development package likely suffers from those issues alluded to above.

---

### Post by tgp1994 on 2017-10-06
Ahh, ok. Thank you for the extended clarification!

---

