---
title: "Broken packages"
date: 2009-06-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by duncan_bayne on 2009-06-12
Hi All,

The xvidcap package is broken in Ubuntu 9.04; it turns out that this problem was reported in 8.10 also and hasn't been fixed inbetween releases.  This isn't the only package that has been broken in multiple consecutive releases, which is pretty bad form.

Is there a plan to list known-broken packages from previous releases, and re-test them in Karmic?  I'm planning to install Karmic myself, so I'd be happy to make a start on working through said list.

Yours,
Duncan

---

### Post by 23meg on 2009-06-12
Can you point to the bug report? What exactly do you mean by "broken"? It seems to work in Jaunty for me.

[QUOTE=duncan_bayne]Is there a plan to list known-broken packages from previous releases, and re-test them in Karmic?[/QUOTE]

The answer to that again may depend on what you refer to as "broken".

---

### Post by Nerd_bloke on 2009-06-12
It is likely [this one]("https://bugs.launchpad.net/ubuntu/+source/xvidcap/+bug/290728"); as stated in the second comment installing libavcodec-unstripped-51 fixes the issue, but it still hasn't been added as a package dependency to fix the bug.

---

### Post by duncan_bayne on 2009-06-13
> **23meg said:**
> Can you point to the bug report? What exactly do you mean by "broken"? It seems to work in Jaunty for me.



The answer to that again may depend on what you refer to as "broken".

By broken I meant "either crashes, or is missing important functionality, after installation with apt-get."

[This is the bug report](https://bugs.launchpad.net/ubuntu/+source/xvidcap/+bug/290728) for xvidcap as pointed out by another poster.  

Another I've recently come across is that [GPA lacks the ability to upload keys using HKP](https://bugs.launchpad.net/ubuntu/+source/gpa/+bug/192112).  Again, unfixed for over a year.

Surely it would be better to identify these packages and remove them from Karmic, than ship stuff that purports to work, but doesn't?  I'm quite happy to assist with this, because I think quality is an important competitive advantage for Ubuntu.

---

### Post by duncan_bayne on 2009-06-14
Oh, and the [Egoboo package is broken in Intrepid and Jaunty](https://bugs.launchpad.net/ubuntu/+source/egoboo/+bug/119536) too.  Needs repackaging, but should be dropped until that's done.

---

### Post by 23meg on 2009-06-16
[QUOTE=duncan_bayne]Surely it would be better to identify these packages and remove them from Karmic, than ship stuff that purports to work, but doesn't?[/QUOTE]

The examples you've cited are part of Universe, which is community maintained. We're already pretty short of workforce in maintaining it, and the effort that would have to go into removing, testing and re-introducing broken packages should instead go into fixing them in place, especially in cases like these where the fix is simple. Such an effort would involve archive administrators (and would put extra work on them for little benefit), and removing a package from the archive lessens the incentive for fixing it. Another point against removal would be that the simple packaging fixes that are required would perhaps be already in place for many users, for whom the package wouldn't be "broken"; I had libavcodec-unstripped-51 already installed, so xvidcap wasn't broken for me.

For concerting the effort on "low-hanging fruit", we have tools and initiatives such as [Harvest]("http://daniel.holba.ch/blog/?p=139"), [Hug Days]("https://wiki.ubuntu.com/UbuntuBugDay") and various [bug lists]("https://wiki.ubuntu.com/MOTU/TODO/Bugs").

---

