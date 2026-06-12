---
title: "Windows Bootloader Gone in Grub"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by jediken21 on 2009-11-18
Hi, kind of a linux newb but I've had windows xp and windows 7 installed on my computer and then I made a separate partition for ubuntu and installed ubuntu 9.10 on that. Now my problem is when grub loads there's no option to boot into windows. I've installed ubuntu several times and windows has always showed up in grub without me having to do anything. What gives? This is really frustrating because I really need to get into my windows partition. Any ideas on how to fix this?

---

### Post by drs305 on 2009-11-18
Do you see the grub 2 menu during boot? If not, hold down the SHIFT key during boot to reveal it.

The first thing to do is to run "sudo update-grub" and see if your Windows install is detected. Sometimes it isn't detected on the installation but is when grub is updated the first time after the install.

Watch the terminal as it runs and see if there are any messages that might provide an indication of what is going on.

---

### Post by jediken21 on 2009-11-18
Ran that command and now it works! That was super easy! Thanks man.

---

