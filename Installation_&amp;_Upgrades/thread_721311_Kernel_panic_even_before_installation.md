---
title: "Kernel panic even before installation"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by spillemw on 2008-03-11
Trying to install Ubuntu server 7.10 over a Fedora Core 4.
When I boot from the CD, if I do "Install" or "Check CD" for defects, I always get the following error :
invalid compressed format (err=1)
Kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block(104,1)

I have tried both the regular and the alternate CD.
I have tried hitting F6 and adding "noapic nolapic nosplash" to the install line.

My system has 1 GB RAM, two SATA HDD of 150 GB each.

---

### Post by rillip on 2008-03-11
it's not an apic error, those will say could not sync to timer or give an explicit apic error.  It appears to be an issue mounting the virtual file system for the CD.  Have you run "check disk for errors?"  It sounds like you could just be burning too high.  Md5 checksum should verify.

---

### Post by spillemw on 2008-03-11
Thanks for answering quickly.
I have the same error when I try to check the CD for errors on the first screen.
MD5SUM doesn't report an issue.

I have burned one CD now at lower speed, but not lowest possible yet.  Perhaps I need to do that?

---

### Post by rillip on 2008-03-11
If you can't check for errors there's definitely a problem.  I'd dele the iso, redownload, reburn.  Could be an ISO corruption, een it happen before from som mirrors.

---

