---
title: "Debootstrap program exited with an error"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by taxpayer on 2005-04-17
I already had a 100 gb Windows ntfs partition, and am trying to install Hoary to the 2 other partitions on the drive.  I got to the disk partitioning part of the installation, all the partitions on the drive were recognized.  I repartitioned the 2  non-ntfs partitions into 3, designating one as swap.  Continued the installation and got

"debootstrap program exited with an error"
"Check  /var/log or see virtual console #3"
"failed to install the base system"

It offered me the option to try again, which I did, with the same results.

Now, when I rebooted the machine, Windows was also unusable.  Working from the windows boot CD, it looks like the windows files, formerly on drive C, are now on drive F.  The ubuntu directories are on what dos considers to be drive C. (I  see a list of directories like home, etc, media, var, usr...  which I assume is ubuntu. )  I can't look inside them because "access is denied"

So my questions are:
(1) What happened?  Did ubuntu put itself on the first partition and move windows?  Or why does it appear that way?

(2) How do I recover windows?  That isn't a problem for this forum, but it will help to know where ubuntu put it.

(3) What went wrong in installing ubuntu? Did I need to tell it in some different way to leave the ntfs partition alone?  I thought it couldn't write to ntfs anyhow, and the partition screens sure left the impression that it would be unharmed.  And why did the install fail?

---

### Post by TravisNewman on 2005-04-18
Looks like you may have had some partition table problems.

as far as number 2 goes, it's not something that Ubuntu would PUT somewhere. If Ubuntu managed to overwrite Windows (which doesn't make sense unless you were having partition table problems), Windows didn't get put anywhere, it got deleted. 

There are ways to recover the drive. Acronis sells a lot of great products for drive recovery, as do many other companies.

As far as why the install failed, that's something that we would need to see. Have you tried installing again? If you do try to install again, check virtual console #3 by pressing ctrl+alt+f3 and seeing what information it gives.

---

### Post by taxpayer on 2005-04-23
I tried installing Hoary once more, with the same result as before, but was able to see /var/log using your sugggestion.  Here it is:

[begin error message]

No volume groups found
Reading all physical volumes.   This may take a while...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
 /dev/sdb: open failed: No medium found
 /dev/sdc: open failed: No medium found
 No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
 /dev/sdb: open failed: No medium found
 /dev/sdc: open failed: No medium found

[all this repeated]

tar: ./usr/share/man/man3/Locale::gettext.3pm.gz: Invalid argument

[end error message]

(It appears that this just repeats, though I can't figure out how to navigate the display.)

If this indicates a partition table problem, it apparently was caused by the ubuntu installer, so I need to find out how to use that correctly or how to work around it.  Suggestions?

---

### Post by FrankieFiggs on 2005-06-11
i have exacly the same problem.. the same error.. there is no answer for that??

---

### Post by taxpayer on 2005-06-11
No answer that I could figure out, and as you see I got no further advice here.  I looked around for an alternative Linux which might have better newbie support, and ended up with Mepis.  I installed it cautiously and successfully, and everything seems to work, though I have barely begun to play with the software.  My Windows partition survived unaffected. 

I installed the 32-bit version as the newest Mepis can't handle 64-bit yet.  I have no idea whether this had anything to do with my better experience.

---

### Post by bluegroper on 2005-08-28
Same debootstrap problems for me.
Trying to install either ubuntu or kubuntu to IBM Thinkpad.
Other linux distros have installed without any bother.
And I checked the CD by using it to install to another desktop machine.  All OK.
Conclusion -> k/ubuntu is not friendly with the underlying thinkpad hardwares.
- BG

---

### Post by bluegroper on 2005-09-02
IBM Thinkpad A22e.

Redhat 7.x and 9.x, and FreeBSD all install OK directly from the CD.
And the ubuntu live CD works fine too.
Really wishing I could make the ubuntu install CD get past the the dreaded "debootstrap" error.  
Tried 2 copies, both failed.  
Also used same CD to install ubuntu to another computer.
Anybuddy got any other ideas ?  ](*,) 
TIA's
- BG

---

### Post by bluegroper on 2005-09-03
No matter.
The network install works fine.
- BG

---

