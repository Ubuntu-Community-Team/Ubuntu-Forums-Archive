---
title: "Need to install ia32-libs"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by Krupski on 2013-11-19
Hi all,

Simple question: How can I install ia32-libs in Xubuntu 13.10?

Now, to save your time and mine, please don't tell me:

* It's depreciated (I know, but I need it anyway)
* APT will handle the dependencies (not if APT doesn't install the package)
* Don't run as root (It's my machine and I'll run as root if I want to)
* Install the 32 bit version of Xubuntu (why have 32 gb of ram then?)
* Search Google (already did... found nothing that works).

What I need, and the ONLY thing I need, is to know how to install ia32-libs in 13.10 the way I always used to in the past.

I want to update to 13.10, but as of now I cannot because a few of the apps that I use all the time NEED the 32 bit support and therefore I'm stuck using 13.04

Sorry for the attitude, but it seem every time a new version of Ubuntu is released, I have to spend weeks fixing and working around all the "improvements" that were added and it's making my head hurt.

Any help will be appreciated. Really appreciated. More than you know.

Thanks.

-- Roger

---

### Post by yc.chenyi on 2013-11-19
Simple answer. No solutions. ia32-libs or any i386 version libs are refused to get into 13.10. Welcome to 64-bit world!

---

### Post by vasa1 on 2013-11-19
> **yc.chenyi said:**
> Simple answer. No solutions. ia32-libs or any i386 version libs are refused to get into 13.10. Welcome to 64-bit world!

+1 from my limited experience.

---

### Post by fantab on 2013-11-19
Yes the support has been dropped if favor of [Multiarch]("https://wiki.ubuntu.com/MultiarchSpec"). 
[http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package](http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package)

If you use a genunine 32bit software then it just works, but not the 64bit version which has ia32-libs dependency.

---

### Post by Krupski on 2013-12-02
> **fantab said:**
> Yes the support has been dropped if favor of [Multiarch]("https://wiki.ubuntu.com/MultiarchSpec"). 
[http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package](http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package)

If you use a genunine 32bit software then it just works, but not the 64bit version which has ia32-libs dependency.

Regardless of what software may be used now or in the future, the bottom line is that ia32-libs, no matter how "bad" they may be, no matter how "depreciated" or "bloated" they may be, **_*made what I need to do work.*_**

I've noticed that the latest release of other Debian based distros still allow installing the 32 bit libs, so it's not a matter of incompatibility.... it's simply a matter of "someone locked it a drawer and won't let me have it".

Given that there is no good reason why I should not be able to use those libs, I can't imagine why I'm being virtually "forbidden" from using them.

There must be a way to make this work........

---

### Post by theantibob on 2013-12-03
> **yc.chenyi said:**
> Simple answer. No solutions. ia32-libs or any i386 version libs are refused to get into 13.10. Welcome to 64-bit world!

Well, that was very helpful of you...

@Krupski
As you can see [here]("http://packages.ubuntu.com/search?keywords=ia32-libs&searchon=names&suite=all&section=all"), ia32-libs has been a transitional package deferring to ia32-libs-multiarch since PrecicePangolin(12.04).
The full removal of this transitional package from SaucySalamander(13.10) obviously isn't working too well, since numerous packages in the repositories still depend on ia32-libs. The Ubuntu development team seems to be adomently opposed to having ia32 anywhere near *buntu, even though a dummy package (at the very least) is obviously required for the time being. [This]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1241327") is the launchpad bug report for ia32-libs not being available in 13.10. The recommended solution is to use the i386 version of your package, and multiarch will handle it.

Which brings me to the real issue: What program are you trying to run that requires ia32-libs? Have you tried installing the real 32-bit package (packagename:i386)? This information will certianly help people help you.

[SUB][SIZE=1]it's google-earth, isn't it[/SIZE][/SUB]

---

