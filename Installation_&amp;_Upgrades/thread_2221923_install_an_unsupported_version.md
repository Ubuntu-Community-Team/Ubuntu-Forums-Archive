---
title: "install an unsupported version"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by Super Joe on 2014-05-04
Hi, I'm a fairly seasoned Ubuntu user, but haven't posted much in this forum.

I have a PC running Ubuntu 11.04 that I would like to upgrade to 14.04, however my version is no longer supported and Update Manager tells me that an upgrade is available but always fails when I start the process.  I was successful in updating by changing my sources to "old-releases.ubuntu.com" (or something similar to that.)  I would like to, however, upgrade my distribution to 11.10, where I then can theoretically upgrade to 14.04.  The problem is that 11.10 is also unsupported too and is only available from "old-releases.ubuntu.com"  I'm not sure how to point Update Manager to that source.:confused:

I know that the common suggestion is to do a fresh install, but I have taken a long time to configure some software packages on this machine to communicate with some custom hardware, and I don't really want to take the time to reinstall the software and configure it.

So, please offer some advise on installing 11.10 and upgrading to 14.04,

-or-

Offer some advise on transferring my current configuration seamlessly into a fresh install of Ubuntu 14.04,

-or-

I'm open to other ideas.

Thanks in advance.

---

### Post by TheFu on 2014-05-04
Being on an unsupported OS sucks.

There are many articles on migrating between Linux systems - that is what you need to consider.  [My backup method]("http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview") is probably the least offensive way to migrate OS versions. Hope it helps.

Also, many, many, many things have changed since 11.04 - things are going to break. Networking is very different now, apache is very different now.  There are huge risks in going from where you are today to 14.04 - expect problems and plan accordingly. Heck, some older hardware won't run 14.04 at all. 

There is NO way to "seamlessly" transfer old configurations - sure, you can copy them over, but newer versions of programs will have different configuration options. Something will break, I'm certain.   Sometimes the programs we've used for years are deprecated too. Gone. The newer method will need to be used and that takes time to discover, understand, solve.

So ... do a test run first to see how well this migration works. Have the ability to drop back to the older system in 10 minutes, if that becomes necessary. Sometimes knowing that an update will break too much ASAP is a good thing.

---

