---
title: "Fawn: Buffer I/O error on device fd0, logical block 0"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by pterandon on 2007-03-27
I downloaded  the Fawn ISO from two different locations, burned to CD.  (In between, I re-burned an Eft CD).


Booting up the Fawn CD (and i think especially when doing a "check CD for defects"), I get a string of error messages which start with

[ 216.089802  Buffer I/O error on device fd0, logical block 0 ]
[other number  Buffer I/O error on device fd0, logical block 0 ]

Any tips?  The messages also eventually start complaining about the mouse.

---

### Post by Saur0n on 2007-03-28
I have this same problem.  Which download mirror are you getting the iso from?

---

### Post by pterandon on 2007-03-28
> **Saur0n said:**
> I have this same problem.  Which download mirror are you getting the iso from?

My recollection is that this happened with an ISO from both  the "Australia"  and the "Everywhere else" ones.

---

### Post by zorkerz on 2007-03-28
Have either you guys checked the disc integrity (checksum) before burning it. It is possible you are trying to burn from a bad iso. The md5sum command gives you a string of numbers that you compare with hopefully an identical string from the place you downloaded.  here this is great [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
It is also good to check thi integrity of the cd when you first boot from it which it sounds like you are doing.  Hope im understanding. Cheers

---

### Post by Saur0n on 2007-03-28
After checking the disk integrity it appears it is a checksum problem however when I run the md5sum on the iso it gives me this output:

> md5sum: ubuntu-6.10-desktop-i386.iso: Input/output error

I've tried 4 different download mirrors so far and they all end up the same way.

---

### Post by Saur0n on 2007-03-28
Finaly found a mirror with a working checksum.  All the checks showed the cd as being fine but the i/o error is still there preventing me from installing.  That's 6 wasted cds now :(

---

### Post by zorkerz on 2007-03-28
Hey guys im afraid i have no idea about i/o errors having never had one.  ive been searching around for i/o errors. Not really finding anything too promising but here are a few seemingly related links.  I have a hunch its hard rive related.
[http://ubuntuforums.org/showthread.php?t=220703](http://ubuntuforums.org/showthread.php?t=220703)
[http://ubuntuforums.org/showthread.php?p=1653875](http://ubuntuforums.org/showthread.php?p=1653875)
unfortunately none of them seem too up to date.

there are a nnumber of posts if you search in the forums for buffer i/o error but i have not found any deffinate solutions
you both have prolly already done this

---

### Post by delta4s on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/97306](https://bugs.launchpad.net/ubuntu/+bug/97306) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the error mentioned in this bug report - [https://bugs.launchpad.net/ubuntu/+bug/97306](https://bugs.launchpad.net/ubuntu/+bug/97306)

---

