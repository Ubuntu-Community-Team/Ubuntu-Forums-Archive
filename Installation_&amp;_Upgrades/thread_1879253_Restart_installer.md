---
title: "Restart installer?"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by Jonathan L on 2011-11-11
Hi All

Q1. After installation of a working Ubuntu server, is it possible to restart the installer program to, for example, configure disks or network interfaces and install packages and tasks?

Q2. Does the installer keep a log of what it's done or make a list of commands?  So that one can write down exactly how a disk is formatted in terms of fdisk etc, and which apt-gets were issued.

Kind regards,
Jonathan.

PS, 10.04 server, if versions matter.

---

### Post by darkod on 2011-11-11
Q1. Once it is installed I don't think you can start the installer to add software without it overwriting the current ubuntu installation.
So you will have to use apt-get install to add the software you want.
Also if by configure disks you mean partitioning, you can use programs like parted or sfdisk (I think it works on server too). Depending what you are used to, it might be little weird with command prompt only, but it's definitely not difficult.

What exactly were you planning to do with the disks and which software to add?
Someone might have instructions on the easiest way to do it.

---

### Post by Jonathan L on 2011-11-11
> **darkod said:**
> Q1. Once it is installed I don't think you can start the installer to add software without it overwriting the current ubuntu installation.
So you will have to use apt-get install to add the software you want.
Also if by configure disks you mean partitioning, you can use programs like parted or sfdisk (I think it works on server too). Depending what you are used to, it might be little weird with command prompt only, but it's definitely not difficult.

What exactly were you planning to do with the disks and which software to add?
Someone might have instructions on the easiest way to do it.

Hi Darkod

Thanks for such quick response.  What I'm doing is creating the instructions for others, and trying to find out the exact sequence of commands that the installer did, or alternatively, just reusing the installer.  So that, for example, if one misses a step during installation one can complete it later with identical results.  And it would be really helpful if the installer wrote it down.

I see of course the things in /var/log/installer, but they're a bit "debug" oriented rather than "repeat" oriented.

So I'm still hoping to find out how to reuse the installer, as in, for example FreeBSD where you can run "sysinstall" at any point.

Thanks nonetheless.

Kind regars,
Jonathan.

---

