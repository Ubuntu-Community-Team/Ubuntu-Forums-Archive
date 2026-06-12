---
title: "USB Printing"
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by sscotti on 2005-09-19
I have a LexMark 715 printer that I finally got working by using RPM available for the driver and installing them using 'alien'.  However, there is a strange or not so strange problem.  It is set up via USB lp0 and the owner of the lp0 device file is root while the group is lp.  When I try to print the printer hangs, but when I change privileges for everyone to read and write it prints to the printer.  I'm not sure who the own of the print job is, but I do have an Apple laser on the same system and it prints to that just fine.  Any ideas on how to fix so that I don't need to change privileges whenever I reboot?

/sds

---

