---
title: "upgrading to 8.04 stalls on Generatin locals"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by Rockling on 2008-09-12
Hi all 

When upgrading from Ubuntu 7 to 8.04 the distribution upgrade hangs on 
Generating Locals

Any fix for this ?

---

### Post by oilchangeguy on 2008-09-12
> **Rockling said:**
> Hi all 

When upgrading from Ubuntu 7 to 8.04 the distribution upgrade hangs on 
Generating Locals

Any fix for this ?

computer specs, and correct ubuntu version, ubuntu 7.?

---

### Post by Rockling on 2008-09-12
> **oilchangeguy said:**
> computer specs, and correct ubuntu version, ubuntu 7.?
Its upgrading from 7.10 
Computer specs
Dell dimension 3200
intel pentium 4 3.2 GHz 2Gig Mem

---

### Post by prshah on 2008-09-12
> **Rockling said:**
> 
When upgrading from Ubuntu 7 to 8.04 the distribution upgrade hangs on 
Generating Locals

Sometimes an upgrade/update seems to hang, but is actually not hung, but waiting for your response to a window; this window can be anywhere on your 4 desktops, and is sometimes hidden behind some other window. Alt_Tab a few times to see if you can find such a window.

---

### Post by snowpine on 2008-09-12
Actually this is a known bug. Check out this thread: [http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)

And the bug report: [https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

---

### Post by Rockling on 2008-09-12
> **prshah said:**
> Sometimes an upgrade/update seems to hang, but is actually not hung, but waiting for your response to a window; this window can be anywhere on your 4 desktops, and is sometimes hidden behind some other window. Alt_Tab a few times to see if you can find such a window.
Hi
Tried alt tab but there was no window waiting for me to do something.
The only window is the Distribution Upgrade window 
This is hung on 

Setting up belocs-locales-bin (2.4-2.2ubuntu7)....
Setting up locales (2.7.9-4)...
Installing new version of config file /etc/belocs/iso-639.def ...
Generating locales...
   en_AU.UTF-8...

its hung there for over an hour

Thanks for the help

---

### Post by oilchangeguy on 2008-09-12
> **prshah said:**
> Sometimes an upgrade/update seems to hang, but is actually not hung, but waiting for your response to a window; this window can be anywhere on your 4 desktops, and is sometimes hidden behind some other window. Alt_Tab a few times to see if you can find such a window.

since when does an operating system play hide and seek with important messages? where do you get your information?

---

