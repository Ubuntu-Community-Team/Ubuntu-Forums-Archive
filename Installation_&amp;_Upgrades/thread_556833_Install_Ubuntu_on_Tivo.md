---
title: "Install Ubuntu on Tivo?"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by juliuss on 2007-09-21
Hi!  I'd like to install Ubuntu on my old retired Tivo box.  I just want it to be a headless system that runs a few little programs and a mysql database.

Does anyone know of a way to get Ubuntu on a box that has no CD drive?  Is there a way to get it on there via USB flash drive?

---

### Post by juliuss on 2007-10-07
Has nobody tried this before?  :confused:

---

### Post by Slim Backwater on 2007-10-07
> **juliuss said:**
> Does anyone know of a way to get Ubuntu on a box that has no CD drive?  Is there a way to get it on there via USB flash drive?

I don't know anything about the TIVO hardware, and I don't think it's based on an Intel x86 hardware, but you could put the TIVO's hard drive into a computer, do the installation there, and then move the hard drive back.

._.

---

### Post by asmiller-ke6seh on 2007-10-07
There may be some real challenges.

The following comes from [http://www.acmqueue.org/modules.php?name=Content&pa=showpage&pid=53&page=1](http://www.acmqueue.org/modules.php?name=Content&pa=showpage&pid=53&page=1) by Jim Barton, co-developer of TiVo. In this artice, "From Server Room to Living Room" he talks about how Open Source came about, use of Linux as the development base of the TiVo, and how Linux is used in the TiVo today.

[B]"The TiVo Client Device is of necessity a closed system. As a service provider, we must prevent theft of service, so TiVo pays a great deal of attention to security of the device and resistance to hacking. Additionally, we sell the TCD at a price that provides a net margin to retailers, but no profit to us. Our profits come from providing service to each device over time, rather than from up-front costs."

"For this reason, it is important that the devices not be re-purposed and that our software not be replaced with other implementations of DVR functionality. Thus, hardware drivers are kept as proprietary sources and are built as loadable modules. Our interpretation of the GPL is that such use is permitted; we are careful to separate these modules from the Linux kernel sources to avoid any confusion. In fact, as has been demonstrated by the very active TiVo hacking community, it is possible to take our published sources, build a Linux kernel, and load it on some versions of the TCD. The kernel will run properly, loading the proprietary modules and executing the TiVo application, thus staying within the GPL spirit."

"This use is somewhat controversial. Advocates of the GPL and the Free Software Foundation interpret the GPL more stringently to disallow the use of proprietary modules. On the other hand, Linus Torvalds has stated that proprietary loadable modules are acceptable. Regardless, the use of proprietary modules has contributed greatly to the explosive growth in the use of Linux and GNU software in general, and is key to the use of Linux in embedded systems. Had this ability not been available, proprietary operating systems would certainly continue to be the norm for most commercial embedded applications."

"GPL software is supposed to be "free, as in free speech not free beer" (attributed to GNU Project and FSF founder Richard Stallman). When such speech is not a modification of another's speech, it should also be recognized that the freedom not to speak must be preserved as a corollary.Under terms of the GPL, if we incorporate GPL-based sources into commercial products, purchasers of such products must have access to incorporated GPL sources."

"TiVo complies with these terms by publishing on its Web site ([http://www.tivo.com/linux](http://www.tivo.com/linux)) the GPL and public domain sources used in each release, along with the tools used to build those sources. The intention is that any interested party would be able to re-create the derived binary versions included in the device using those sources. No proprietary software is included in these sources."

"During development, TiVo may modify these sources. These modifications are included in the sources made available on the Web site, again under provisions of the GPL. From time to time, TiVo also makes some of its proprietary developments available under the GPL or as public domain sources for the benefit of the developer community. For example, TiVo has released a software development kit as part of its Home Media Option (HMO), a software application for the TCD that enables the playback of music or digital photographs across a home network from a personal computer, allows transfer of programs among TCDs in the home, and provides the ability to schedule the recording of programs from a remote Web browser. This kit documents our network protocols and provides sample code for a server application (see http://www.tivo.com/developer)."

"At TiVo we believe that making our modifications and enhancements to these sources generally available is part of our contribution back to the open source community and is an acknowledgment of the value that open source has brought to our products. As we neither sell nor distribute the software used in development and in the TiVo Service itself, we do not publish the underlying GPL-based or public domain sources."
[/B]

---

