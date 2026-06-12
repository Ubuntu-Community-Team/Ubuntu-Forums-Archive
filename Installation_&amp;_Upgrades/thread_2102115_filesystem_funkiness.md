---
title: "filesystem funkiness?"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by ray field on 2013-01-06
Something weird going on in my Precise install.

I am actually deliriously happy using Quantal, especially since Compiz functions much more smoothly there for me, but since I want to commit to an LTS (even if Canonical doesn't!), would like to get Precise running stably.

So, since I hadn't booted from that partition in a few months, I tried last night, and first thing I did was to run software updates. This didn't go smoothly -- had to reboot once or twice to get these to complete. Oddly, the update process gave me a diskspace warning, which rebooting *seemed* to solve.

At first I thought the reason reboot brought the "low-graphics mode" screen up was maybe because grub was messed up. I booted to the Quantal partition and ran boot-repair, but the problem with the Precise partition persisted. 

Nothing I tried seemed to work, eg, removing and reinstalling xserver. Moreover, eventually I discovered I was having problems writing to disk (though "apt-get install" operations seemed to complete. "df -h" showed me plenty of free space. But something still seemed amiss -- when I or recovery mode tried to run fsck, the process would hang. 

Also, on bootup, the screen fills with line after line of "end-request i/o error" messages.

I rebooted to the Quantal partition and kicked up gparted. fsck completes successfully on the partition, /dev/sdb1. 

This morning I tried again -- seemed to get farther, that is, removing and reinstalling xserver *seemed* to work, but when I tried xorg-configure, I got "unable to write/open X configuration file" "unable to write to directory /etc/x11," so something still seem wrong with the fs.

---

### Post by ray field on 2013-01-08
bunkmpt

---

### Post by ray field on 2013-01-10
sbumpnk

---

