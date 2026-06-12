---
title: "&quot;Failed to create a file system&quot;, 15% error? try Alternate CD install"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by crimson117 on 2006-06-15
In case anyone else experienced this problem... 

Some people have reported problems such as "Failed to create a file system", and an error at 15% using the LiveCD installer.

[http://justinsomnia.org/2006/06/giving-ubuntu-another-go-with-dapper-drake/](http://justinsomnia.org/2006/06/giving-ubuntu-another-go-with-dapper-drake/)

We found using the Alternate Install worked without any issues.  The dialog boxes and information asked in the Alternate install were the same as in the LiveCD graphical install, and just as clear - though slightly less pretty.  I don't think "text installer" does it justice.

Using this alternate installer is probably good advice for any install problems users run into with the graphical installer.

:KS

---

### Post by kbkealiher on 2006-06-15
This worked for me. I tried without success to install Dapper Drake using the standard i386 iso image. I downloaded the alternate installation image, and made sure to burn it to CD at 4X. Once that was done, I was able to install with no difficulties at all.

---

### Post by TeeAhr1 on 2006-06-15
I had the same problem.  Another thing that worked for me was this: Instead of using the partitioner in the install program, use Gparted before starting Install.  It's included in the Live CD, System > Admin > Gnome Partition Editor.  Gparted had no problem partitioning my drive correctly.  YMMV.

---

