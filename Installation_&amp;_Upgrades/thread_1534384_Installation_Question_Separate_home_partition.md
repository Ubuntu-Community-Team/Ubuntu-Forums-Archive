---
title: "Installation Question: Separate /home partition"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by pmulgaonkar on 2010-07-19
I have an installation question that I need help on. I tried upgrading from 9.10 to 10.04 and now my machine will not go past the ubuntu screen. So I am considering a fresh install from the Live CD. My system is configured with its /home on a different partition from the /. 

When I get to the first part of the install process, the choices are to (a) install 10.04 in a parallel partition to the existing broken 10.04, (b) completely reformat the existing disk, or (c) custom.

In custom, I can specify the partition to use for the new install. It also allows me to indicate the partition where /home will go. But I want to ensure that pointing the new /home to the existing /home partition _will not erase the existing data on /home_. The wording is not very clear. There is a format check box which I can leave unchecked. I assume that is what the semantics of the installation are.

Am I correct? Can someone verify that for me please?:

--prasanna

---

### Post by oldfred on 2010-07-19
Yes you have to use the manual install and choose each partition / (root) and what format, and /home but then have to be careful to make sure you do not format it. It seems to find your existing swap without any issue.

I prefer to set up partitions in advance and then do the install choosing partitions & formats.

---

### Post by pmulgaonkar on 2010-07-22
Thanks. I did that and am back up and running. But now I have to remember all the apps I have to reinstall.

--p

---

