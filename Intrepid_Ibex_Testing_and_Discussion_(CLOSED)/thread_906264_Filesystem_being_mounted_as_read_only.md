---
title: "Filesystem being mounted as read only"
date: 2008-08-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2008-08-31
I am sure a bug will already have been raised about this, however I thought I might check that anyone else is suffering from this. 

I am using ext3 journaled and after a certain amount of times mounted it performs file system check. 

However it is not doing this in intrepid, it fails to perform the check and always mounts the drive as read only. 

The only way I have found to fix it is to boot from the live cd and then fsck from there. After that reboot and it works quite happily

George

---

### Post by plun on 2008-08-31
"RAOF" has reported 2 bugs
[B]
Parallel fsck leads to unhelpful error message at login[/B]
 [https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255562](https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255562)
[B]
Parallel fsck breaks boot when / is being fsck'd[/B]
[https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255563](https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255563)


Discussed within this thread:
[http://ubuntuforums.org/showthread.php?t=894747](http://ubuntuforums.org/showthread.php?t=894747)


I just waits as RAOF confirms on page 2.

---

### Post by g-robbie on 2008-09-02
at the grub splash hit escape and choose recovery mode - the disk is then mounted read/write and fsck can do its thing; then you can boot as normal.

---

### Post by Peter76 on 2008-09-02
I also had this problem; then rebooted in recovery mode and ran fsck manually.... This absolutely screwed up my Intrepid install. Have to reinstall and see if I can reproduce. Watch out here

---

