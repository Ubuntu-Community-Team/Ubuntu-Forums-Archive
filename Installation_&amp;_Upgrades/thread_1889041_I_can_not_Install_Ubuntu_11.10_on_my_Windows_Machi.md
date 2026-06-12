---
title: "I can not Install Ubuntu 11.10 on my Windows Machine, Help !!"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by papan2005 on 2011-11-30
Hi Friends,
           I have my OLD mercury board machine with the following configuration:-

RAM 512 MB
Hard Disk 200 GB
Processor 1.8 GHz
Mercury Motherboard 845GL model [ 6 Years OLD Machine]

Currently, Windows XP OS is installed in my machine. I want to install Ubuntu 11.10 alongside  with Windows XP. During Installation Ubuntu on Windows XP, The following Error "iso_path" has come and then Ubuntu installation get stopped.:confused:

See Screenshot of this Error message:-

[IMG]https://lh4.googleusercontent.com/-dpqK5rwkbD8/TtZ1zXeogWI/AAAAAAAABOY/gs4lW9b5F90/s640/untitled.JPG[/IMG]

Every time when I start installation from USB stick, this error message has shown. I can not install Ubuntu in my machine.

I need expert help to resolve this issue and How can I install Ubuntu successfully.:confused::confused:

Thanks,

Papan

---

### Post by darkod on 2011-11-30
This is installing wubi inside windows. Not a dual boot of ubuntu and windows.

But I have no idea why this error is showing up, I never use wubi.

---

### Post by deonis on 2011-11-30
Boot from life CD, use gparted to make some space for the new installation. Install ubuntu side by side with windows. That's all :)

---

### Post by bcbc on 2011-11-30
Post the logfile: %temp%\wubi-11.10-rev241.log

Unfortunately wubi messages aren't very helpful unless you look in the logfile.

---

