---
title: "Moving an LVM xUbuntu install to a different hard drive?"
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by jwesleycooper-n on 2016-07-31
I have xUbuntu LTS and Windows 10 installed on the same physical HDD, with the Ubuntu side configured using LVM so I can dynamically allocate root and home partitions if necessary.  However, I was recently given a small (<100GB) SSD, which I want to use for the initial placement of my root linux filesystem to increase performance.  However, since LVM is already involved I need to know ... is it possible to format and configure the drive to use LVM in such a way that it prefers space on the SSD over the HDD for root and if so how do I do this and how would I move the current install (bootloader included) in such a way that it will not break my current multiboot configuration?

---

