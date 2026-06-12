---
title: "New install on new system - how to migrate all settings/programs"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by james25182 on 2012-05-27
Hi.

I've been running Ubuntu 10.10 for a while now mainly as a home server. I've just bought an upgraded box that can fit some more drives in as my old system only had room for one (an HP ProLiant Turion II N40L MicroServer if anyone is interested).

I want to install the latest 12.04 LTS version on the new server. What's the easiest way to move/reinstall all the programs I have running on my old server and keep as many settings the same as before? From memory I'm running the following:

SAMBA
Sickbeard
SabNZBd+
CouchPotato
mySQL
Memopal Backup

But there's probably more that I've forgotten. All my data is on a single drive that I'll move over but I'll be installing 12.04 on a fresh drive in the new system.

Thanks!

James

---

### Post by james25182 on 2012-05-28
Bump. Any help?

---

### Post by oldfred on 2012-05-28
I do not know servers and your specific apps. Do they have their own directories in / (or not in /home) to store data?

With a desktop you would just need to copy /home for all user setttins and data  and export a list of installed applications, possibly some custom system settings from /etc.

I gave up on Samba as it seemed every update in XP on my laptop system, firewall or virus software messed it up. So I just installed Ubuntu to the laptop and now use NFS to copy data with my Desktop. I know those settings in several places but just scripted the update as I regularly reinstall another version of Ubuntu.

This really is just for a desktop:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Since you will have old hard drive, I would just install to new system and temporarily mount old drive in new system to copy data over that you need. Just do not copy old settings unless you are sure you need them as new settings may conflict.

---

