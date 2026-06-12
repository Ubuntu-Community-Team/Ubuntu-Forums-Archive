---
title: "Reinstall on '/' partition, save /home partition"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by jcr1 on 2008-05-04
Hi all,

I just set up my install on 3 partitions: 1) '/' 2) '/home' 3) swap.

This is obviously a good setup so that if and when you need to reinstall, you don't need to backup/restore your home directory and settings.

My question is, when I do reinstall, how does it know I already have a home directory setup? i.e. when installing, will it try to create a fresh /home? how do I tell it, 'I already have one... here it is... don't create a new one'.

---

### Post by bulldog on 2008-05-04
When you do a reinstall,choose manual partitioning,and mount / as / and set it to format.
Mount /home as /home and DO NOT format.
Should be going fine.

---

### Post by ssican on 2008-05-04
There is a webpage that describe the method of to change, rename the name of the personal home directory into (/home).

"Then, I went into /home and renamed my personal home directory from &#8220;rick&#8221; to &#8220;rick-old.&#8221; The purpose of this was to keep all my personal settings and data (which were previously located in /home/rick/) in a separate directory so that Kubuntu 8.04 could create a fresh &#8220;rick&#8221; directory with the new OS version&#8217;s default settings, unencumbered by any of my own customizations and without trouncing on any of my precious data &#8212; always a good idea with a major new OS release." Source: [http://www.deviceguru.com/2008/04/28/hardy-heron-moves-into-the-black-tower/](http://www.deviceguru.com/2008/04/28/hardy-heron-moves-into-the-black-tower/)

The (/home) directory is not formatted.

---

### Post by haiji on 2008-05-04
> **ssican said:**
> There is a webpage that describe the method of to change, rename the name of the personal home directory into (/home).

"Then, I went into /home and renamed my personal home directory from &#8220;rick&#8221; to &#8220;rick-old.&#8221; The purpose of this was to keep all my personal settings and data (which were previously located in /home/rick/) in a separate directory so that Kubuntu 8.04 could create a fresh &#8220;rick&#8221; directory with the new OS version&#8217;s default settings, unencumbered by any of my own customizations and without trouncing on any of my precious data &#8212; always a good idea with a major new OS release." Source: [http://www.deviceguru.com/2008/04/28/hardy-heron-moves-into-the-black-tower/](http://www.deviceguru.com/2008/04/28/hardy-heron-moves-into-the-black-tower/)

The (/home) directory is not formatted.

Wow, this is a really good idea. I used to remove all files preceded by a dot.. Very rudimentary lol

---

### Post by jcr1 on 2008-05-05
Cool cheers for that guys

---

### Post by Mutikasa on 2011-12-19
what about swap?

---

### Post by satanselbow on 2011-12-19
> **haiji said:**
> Wow, this is a really good idea. I used to remove all files preceded by a dot.. Very rudimentary lol

Very much depends whether you want to "reset" your configuration or not - can be a good idea when your DE of choice has had a major upgrade. Certainly necessary if you are planning on a move from KDE -> Gnome for example as a tidying up excercise ;)

It has been somewhat necessary with some of the Gnome-shell updates for example as configurations develop - quite pertinent with regards to shell extensions.

You can of course retain your firefox profile (and many other app configs) by retaining their respective ~/.appname
 folder ;)

---

