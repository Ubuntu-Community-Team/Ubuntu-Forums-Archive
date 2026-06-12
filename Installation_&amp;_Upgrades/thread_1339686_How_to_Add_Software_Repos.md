---
title: "How to Add Software Repos?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by foresthill on 2009-11-27
Hi all,

I am a refugee from Open Suse 11.2, which appears uninstallable on my laptop due to never-ending ATI graphics-related crashes.

Open Suse has YAST for adding software and seems to do a good job at finding the latest versions of software. However with Ubuntu 9.10, I tried to get Opera browser installed, but the Synaptics Package Manager seems unable to find a source for it.

Also, I installed Wine from the terminal, and it installed fine, but it was a very old version.

So this tells me that I need to add some better software repos. If this is indeed the case, does anyone have a list of reputable repos I can add, and could you you also tell me how to add them. Thanks in advance!

---

### Post by Chargaff on 2009-11-27
Hi,

There are plenty of ways to install Opera on Karmic. Google with "installing opera karmic" will lead you to different easy solutions.

To add softwares repos, you can do it via Synaptic or by editing /etc/apt/sources.list.

---

### Post by snowpine on 2009-11-27
Nothing is "better" than Ubuntu repos. They are slightly out of date because Ubuntu is a "stable, time-based release" distribution (by design), not "rolling release" like Arch or Sidux.

You might be interested in the Backports repository. It is an official and trusted way to get newer versions of selected applications: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I would recommend getting the latest Opera and Wine from the Opera and Wine websites, respectively.

---

### Post by sisco311 on 2009-11-27
opera:
just install the deb from the opera site; it will add the repo to your sources.list

wine: 
[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

---

### Post by foresthill on 2009-11-27
OK, I'll do that. I guess I'm used to the Suse repos which seem to have fairly new versions of everything. It's probably better to get software directly from the source anyway.

Apparently Ubuntu places more emphasis on security updates than third party apps, which is as it should be. Thanks for the help.

---

### Post by audiomick on 2009-11-27
what snowpine said...

---

### Post by wilee-nilee on 2009-11-27
Add the Ubungtu tweak ppa to thge source list and you acn get all kinds of ppa's and others keys and all.
[https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa](https://launchpad.net/~ubuntu-tweak-testing/+archive/ppa)
This is the unstable but I have never found it be
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)
Here is the stable.

---

