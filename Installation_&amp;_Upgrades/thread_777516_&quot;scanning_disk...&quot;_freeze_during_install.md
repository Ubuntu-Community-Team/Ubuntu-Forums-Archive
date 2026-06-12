---
title: "&quot;scanning disk...&quot; freeze during installation"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by lucidlion on 2008-05-01
During installation of ubuntu 8.04 (I have also tried kubuntu) the setup freezes while the "starting up" window is displayed.  It gets stuck at 46% with "scanning disks...".  I have tried installing with and without the graphical interface with the exact same result.  This is a brand new system with Windows XP installed.  I have also tried defragging the disk and checking for errors.  Always I get the same crash at 46% of "scanning disk".  I have also tried multiple CDs and one of the CDs worked fine on a different system.  Any ideas?

---

### Post by bigred1 on 2008-05-01
I have this same problem, too. Right after upgrade, the boot process hanged after giving the output shown below. Even after 8 hours the process still hangs.
 
A hard-reboot seemed to cure it, but now it shows the same behavior erratically, every third reboot or so. Hard re-boot is a workaround, but not acceptable as a solution.

This is a very severe bug. (Should I report it as a bug? )Help 
will be greatly appreciated. 

By the way, the output below shows a "fail", but the process continues, so I think that that is not the real problem.

Also, though the fsck never gets beyond stage 1/5 , I sense that that is not the problem either.

```

* Loading manual drivers... 	[OK]
* Setting kernel variables 		[OK]
error: "vm.mmap_min_addr" is an unkown key [fail]

* Activating swap 				[OK]
* checking root file system...
1206
fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 has been mounted 21 times without being checked, check forced
checking drive /dev/sdb1: 0% (stage 1/5 0/1147)
/dev/sdb1: 178559/18792448 files  (2.7% non-contiguous), 7612916/37561970 blocks
```

---

### Post by fontanar on 2008-10-27
Hi there,,, 

I have a similar problem, but not exactly the same. 

I have Ubuntu 7.10 on an HP laptop (AMD-64, AthlonX2), which is running Vista on the primary partition.  

I had been using Ubuntu for a few months, but several weeks ago (I haven't fixed it yet, and it's still happening), I started having the following issue: 

I turn the computer on, Grub selects the default boot (which is Ubuntu), I get the graphical logo, and orange bar, and then it goes to an fsck, and eventually gives the following message: 

*/dev/sda4 has been mounted 34 times without being checked, check forced...*

and then it start sscanning, but it gets to a certain percentage, and it hangs there forever.  The percentage is never the same.  Sometimes does not go over 6%, and the maximum it has reached is 84.4%, but it's never the same number. 

I have even left it running over night (about 20 hours), trying to give it all the time in the world, but it still hangs.  There is no way to pass this point of 'fsck'. 

I have seen other threads in here, but in all of them (unless I missed the right one) eventually the scan goes thru, and the boot succeeds.  The replies mainly talk about how to change the frequency of the scan. 

That's not my case.  In summary, I cannot use Ubuntu, and I had done a lot of work before.  I wouldn't like to reinstall since I would lose all my data. 

Any help out there??? 

Thanks in advance, 
Roberto

---

