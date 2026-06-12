---
title: "tell me there's an undo for the partition table, PLEASE"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by TechnoJunky on 2008-04-30
I've totally messed up.  I tried upgrading (new install) to 8.04.  I picked manual and selected sdb1 for the installation.  I had my hard drive setup with 3 partitions, root (sdb1), home (sdb4) and swap (sdb5).  I formatted sdb1, but afterwards couldn't boot.  I retried it several times and gave up and decided to go back to 7.10.  This time it booted to a trial OS and I mounted sdb4 and while it was mounted went to do the install.  I selected guided and picked sdb partition 1.  I thought it would only destroy partition 1 (sdb1).  It said it failed, but my mounted sdb4 was still accessible, and mounted.  I thought maybe having it mounted may have caused a problem, so I unmounted and went back into the install program.  This time under manual I didn't see sdb4 listed.  I went back to konsole and remounted sdb4, everything was there.  I assumed that the install program was having an issue so I rebooted.  Now it's still not listed and I can't mount it either.  Is there anyway to get my sdb4 back?  Is there an un-fdisk program?

---

### Post by TechnoJunky on 2008-05-01
I also posted this on LinuxQuestions.org.  I got a reply there to try 
[http://linuxappfinder.com/package/testdisk](http://linuxappfinder.com/package/testdisk).  It worked, I got my home partition back.

---

