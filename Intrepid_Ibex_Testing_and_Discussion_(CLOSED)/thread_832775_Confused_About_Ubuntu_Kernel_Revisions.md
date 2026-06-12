---
title: "Confused About Ubuntu Kernel Revisions"
date: 2008-06-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-06-18
I see some good fixes going into the Linux kernel on kernel.org. For example in 2.6.25.x and 2.6.24.x. I know hardy is on the 2.6.24.x tree. Some questions:

1. How do I know what version Hardy is on given Ubuntu modify the name. i.e. Is it 2.5.24.7 (latest) + Ubuntu patches?

2. When I see for example a device driver fix in 2.6.25.7 that was released on 16/06/08 I dont see that "backported" into 2.6.24. Some of the device driver fixes are for my hardware too. So, how do I get these fixes without having to compile my own kernel? Does Ubuntu keep looking at higher up linux code changes to include as patches into its revisions?

Thanks

---

### Post by Game_boy on 2008-06-18
Hardy does kernel updates with patches from upstream and Debian. We're on Hardy revision 19 at the moment.

It doesn't match up with the upstream kernel updates though. Possibly some changes are unsuitable for SRUs. If you _need_ the latest hardware support, upgrade to the development version Intrepid.

---

### Post by chrisccoulson on 2008-06-18
If you need the latest hardware support, then upgrading to Intrepid _is not_ the answer for most normal users. The answer is to report a bug on Launchpad so that the necessary changes can be made as a SRU (if suitable), or a driver can be added to the linux-backported-modules packages

---

### Post by Nullack on 2008-06-18
> **Game_boy said:**
> Hardy does kernel updates with patches from upstream and Debian. We're on Hardy revision 19 at the moment

Thanks, so where can I lookup that hardy revision 19 has the fix for a device driver from the kernel 2.6.25.7 patch?

See what Im getting at about this confusion? Or is there an easy way?

---

### Post by 23meg on 2008-06-18
[QUOTE=Nullack]So, so where can I lookup that hardy revision 19 has the fix for a device driver from the kernel 2.6.25.7 patch?[/QUOTE]

[http://kernel.ubuntu.com/git](http://kernel.ubuntu.com/git)
[https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide)

---

### Post by chrisccoulson on 2008-06-18
It won't contain (or is unlikely to contain) the patches you speak of unless someone has requested them on Launchpad. Please have a look at [https://wiki.ubuntu.com/KernelUpdates]("https://wiki.ubuntu.com/KernelUpdates") for an understanding of how kernel stable release updates are managed.

---

### Post by Nullack on 2008-06-18
Ive been thinking about this overnight....Isnt this all a bit flawed? Scenario:

New Linux user tries Ubuntu out
Has a crash from a bug in a linux kernel drivers
Doesnt know about future Linux code changes, software lifecycles and all the rest of it
Lets say, this person is unusual in that he actually reports a bug on the problem
Theres tens of thousands of bugs in the database and not all of them get looked at by qualified people who are able to determine that upstream patches not in the Ubuntu builds will fix it


Seems to me the idea of "supporting" an Ubuntu distro requires the kernel team to be continually monitoring all patches ahead of Ubuntu revisions and pushing down all real fixes.

Bugs in device drivers are in my experience probably the worst aspect of Linux reliability. And, submitting a bug doesnt mean the issue will be addressed.

---

### Post by Amaranth on 2008-06-19
Please hire a dozen kernel hackers to work on this.

Usually almost no changes go into kernels after we've had a stable release, hardy seems to be changing that but I have no idea to what extent.

---

### Post by Nullack on 2008-06-19
One of the things Ive been dreaming of is being wealthy to the point I can donate large sums to Ubuntu :) However, thats not the case.

The criteria for what constitutes a "stable" release is not exhaustive or fool proof. Bugs will be identified post the "stable" release. In my experience most of the serious ones will be in device drivers.

I personally do what I can to report bugs and diagnose issues down to clear repeatable steps. Countless others too help out, and thats great. Us enthusiasts do what we can.

I'd like to point out that in the interests of Ubuntu being a leading distro that "just works" and for people who are testing the waters of Linux they can get into a negative situation quite easily due to these upstream bug fixes not being in Ubuntu revisions that are apparently under "support". Its not just old Nvidia drivers being a problem either, its other open source device drivers that are not robust.

It would be a great shame to come to the conclusion that Ubuntu isnt able to resource the people needed to support the distro. I guess with that I can also justify it being a great shame I am not obscenely rich so I could donate most of my money to the project :)

---

