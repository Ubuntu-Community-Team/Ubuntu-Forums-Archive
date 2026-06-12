---
title: "Installer wiped my partitions without appropriate warning - furious!"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by DrPotoroo on 2014-03-20
Recently purchased a surface pro with the plan of primarily running some flavour of linux and having the option to boot to windows for a small handful of situations where it is impossible to do something without windows.

I shrank the windows partition and installed ubuntu 13.10 first. No problems except I have a specific requirement of my window manager that unity won't meet. So I started looking at alternatives. Tried mint but had wifi issues and the surface pro would never power off on shut down. Next I decided to try xubuntu.

Running off the usb xubuntu looked promising. So I ran the installer. Now, when it gave me options to "refresh" ubuntu, wipe and reinstall ubuntu or "do something else" I would usually choose "do something else." However, I thought for simplicity I would try the wipe & reinstall option. Although the description only referred to clearing the ubuntu partition, I thought there was a risk it might wipe windows but assumed it would tell me exactly what it was going to do to my partitions at a later step and have me confirm.

I was wrong.

The install reformatted AND repartitioned my entire drive, and gave me no further warning it would do so. Windows gone. Windows recovery partitions gone.

Anyway, it was a brand new computer and my wife also has one with intact recover partition. So I didn't lose much other than time.

But I could have.

Should I be reporting this as a bug?

---

### Post by ubfan1 on 2014-03-20
Sure, even adding just the word "disk" after "wipe" would make the choice less ambiguous.

---

### Post by Mark Phelps on 2014-03-21
> Should I be reporting this as a bug? 

The problem of having the entire drive reformatted automatically when reinstalling or upgrading an existing Ubuntu installation has already been reported ... but sorry, don't have the specific "bug" information.

---

### Post by DrPotoroo on 2014-03-23
Thanks. I was able to find the bug report: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1266437?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1266437?comments=all)

If anyone else is affected, log files are wanted from /var/log/installer after the install. I and others affected this had already overwritten the install before making a bug report.

---

