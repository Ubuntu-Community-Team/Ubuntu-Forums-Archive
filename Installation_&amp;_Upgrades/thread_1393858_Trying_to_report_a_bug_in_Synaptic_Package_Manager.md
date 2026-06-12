---
title: "Trying to report a bug in Synaptic Package Manager"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by abisdad on 2010-01-29
Hi,

Middle of doing an ordinary weekly package update, my Acer Aspire One (ZG5) netbook went into some kind of power save mode and refused to come back. On re-boot the file system was corrupt, so I recovered it using e2fschk and logged in satisfactory.

When I tried to run Synaptic Package Manager, I come up with:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_karmic-updates_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

So I click the close button and SPM closes.

I've tried to run ubuntu-bug to report the problem, but if I enter ubuntu-bug Synaptic Package Manager in a Run Application window, nothing seems to happen.  If I run System Monitor to find the PID, I cannot see either Synaptic or System Manager there.

So how do I report this?  I would love to try to if I can.

Also how can I reinstall SPM using the command line too?

Thanks,

Rob. :-)

---

### Post by kansasnoob on 2010-01-29
Open Synaptic, click on Help > Report a problem to file the bug report.

The package name is just synaptic.

---

### Post by kansasnoob on 2010-01-29
Just noticed this:

> /var/lib/apt/lists/**[COLOR="Red"]au[/COLOR]**.archive.ubuntu.com_ubuntu_dists_karmic-updates_multiverse_binary-i386_Packages

Try changing from the Australian server to the main Server. To do that in Synaptic go to Settings > Repositories. It's obvious under the Ubuntu Software tab.

---

### Post by abisdad on 2010-01-31
Thanks for your reply.

Unfortunately Synaptic Package Manager closes as soon as I click the close button to the message.  So I can't click on Help > Report a problem to file the bug report.

Even before I click close on the Synaptic Package Manager message, I cannot find the Synaptic Package Manager's PID when I run ubuntu-bug to report the problem either.

Any ideas on how I should proceed?

Thanks,

Rob

---

### Post by Soul-Sing on 2010-01-31
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by abisdad on 2010-02-02
Thank you leoquant,

Looked as if it was working OK...  Until the end!  See below:

Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Sources [23.8kB]   
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Sources [3,831B] 
Fetched 554kB in 7s (75.7kB/s)                                                 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I've no idea now! Any suggestions?

Thanks for your time,

Rob.

---

### Post by Soul-Sing on 2010-02-02
Yeah, please close all other packagemanagers,( synaptic/add remove software) or -apt or dpkg, and then run:
```
sudo apt-get update
```

---

### Post by abisdad on 2010-02-03
Thank you leoquant!

Success!

I hadn't realised that I had Update Manager still open.

Ran 'sudo apt-get update' and then Update Manager started automatically, and I'm currently running an update.

Very grateful for your help.

Rob

:popcorn:

---

### Post by Soul-Sing on 2010-02-03
Your welcome :)

---

