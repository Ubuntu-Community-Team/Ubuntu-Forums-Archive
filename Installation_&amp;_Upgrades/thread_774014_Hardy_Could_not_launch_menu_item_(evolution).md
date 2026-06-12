---
title: "Hardy: Could not launch menu item (evolution)"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by enoughsaid05 on 2008-04-29
Hi all,

I am having a problem with my evolution. I am using Hardy.

I just did a upgrade and it says my upgrade was still not complete. I was a bit intrigued because I thought I have already upgraded everything. So I just went along with it anyway.

It removed some of the files, including evolution and put in a new one called "evolution mail and calender". After the upgrade, I couldn't launch evolution. A window appeared and said," Could not launch menu item, Failed to execute child process "evolution" (No such file or directory)". I went to the Add/ Remove Application to install evolution but it says, 

"Cannot install 'evolution'

This application conflicts with other installed software. To install 'evolution' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

How do I resolve the problem?

---

### Post by Kevbert on 2008-04-29
That's very interesting.  I did a fresh install of Hardy.  I then decided to install QtParted via Add/Remove and got a similar error when I tried to run it.  I've raised a bug report on this which can be found here: [https://bugs.launchpad.net/ubuntu/+source/qtparted/+bug/223852]("https://bugs.launchpad.net/ubuntu/+source/qtparted/+bug/223852")
As soon as I get a reply I'll let you know.

---

### Post by locovaca on 2008-04-29
This happened to me too.  Evolution-Data-Server was updated, but it forced evolution to uninstall and some other libraries.  Now E-D-S is at a version that conflicts with Evolution and it won't install.  I'm running amd64 version and upgraded from 7.10.  I'm going to try to downgrade to the last version I had installed to see if that helps.

---

### Post by Kevbert on 2008-04-29
Hi.  I've added a link to this thread in launchpad (where my bug report is).
Hopefully this will be looked at soon.

---

