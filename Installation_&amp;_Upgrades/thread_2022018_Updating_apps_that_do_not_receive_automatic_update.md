---
title: "Updating apps that do not receive automatic updates"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by slalala on 2012-07-10
Please don't kill me, this may be an easy question that has been asked for over a zillion times before. So I do apologize.

Most programs I install in the (sluggish) Ubuntu Software Center don't seem to receive automatic updates. So I get stuck with older versions of programs. Is there an easy way to change settings somehow so I can update about everything that is installed on my laptop? I don't like messing with tarballs very much. 

Thank you very much!

---

### Post by SlugSlug on 2012-07-10
By Default Ubuntu laggs behind a bit with new updates (eg firefox versions)

You can add PPA's for software so update manager will supply you with the latest firefox. This can cause some problems with other apps so I wouldn't add every PPA you come across


The easiest way I find is to install Ubuntu Tweak in there for example again, you can add Firefox stable PPA

---

### Post by Cheesehead on 2012-07-10
> **slalala said:**
> Most programs I install in the (sluggish) Ubuntu Software Center don't seem to receive automatic updates. So I get stuck with older versions of programs.

Perception, but not reality.

Software Center programs get updated at the same time and in the same way as the install CD programs. Your system can't tell the difference, and treats them equally.

---

### Post by slalala on 2012-07-10
So this means that my programs get updated every six months, if there are any updates? And assuming the programs are still included. That basically means I have to install all updates manually, if I want them sooner. Maybe I should try not to be a spoiled brat and learn to install tarballs. That ppa stuff is another solution of course but if it is not recommended I won't do it. I don't use firefox by the way. Do you guys have any experience with system problems after updates? It seems like the automatic updates are causing some trouble.

Thanks for the respones!

---

### Post by Cheesehead on 2012-07-11
> **slalala said:**
> So this means that my programs get updated every six months, if there are any updates? And assuming the programs are still included.

Packages can be updated at any time, and more frequently than the next release...if the upstream release is important enough to justify it.

If the new upstream release fixes a critical bug, please file a [Stable Release Update]("https://wiki.ubuntu.com/StableReleaseUpdates") (SRU) request on the Ubuntu Bug Tracker.

If the new upstream release does not meet the criteria for an SRU, then please test it for compatibility with your current Ubuntu release, then file a [Backport]("https://help.ubuntu.com/community/UbuntuBackports") request.

Should you learn to install tarballs? Sure, on general principles. You should also learn to package. If the Ubuntu Backporters can trust that your backport requests are correct and pre-tested, then you're saving them a lot of effort and they are likelier to address your request sooner. You help **all** of your fellow users that way.

If the program is still actively maintained upstream, it will still be included in the next release of Ubuntu. Only abandoned, unmaintained projects get dropped. Dropped projects that get ressurected or forked can be added again. In other words, this is something 100% within the control of you and the other users of any package.

---

### Post by kelvin spratt on 2012-07-11
The easiest way to answer your question is Ubuntu is not a rolling release its a 6 monthly cycle so most updates are security based. Siduction/Archlinux/Sabyon/Gentoo etc are and get the latest and greatest without a lot of testing as they are released. Others like pclinux/Chakra are rolling releases but use more mature updates. Then comes a myrad of Debian safe very mature long release cycles.

---

