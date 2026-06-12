---
title: "How does one suggest something to the developers?"
date: 2009-11-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dullstar on 2009-11-15
I think it would be a good idea to allow users to choose between the newer Grub2 or the older Grub.  Of course, the main reason for this is that Grub2, well, hosed my system, but I'll hand this to Grub2:  there's a chance that instead of being a Grub2 issue, a vital Windows file may have broke during partitioning and I never found out.  

So, how do I suggest this to developers?
I know I won't have to do it about choosing between ext3/ext4, though, as the way the partitioner works, I could set it to ext2 if I wanted to.  Not like I would, but I could.  I prefer ext3 just because I really don't have any use for being able to support a hard drive size larger than any hard drive ever created and then some (doesn't ext3 do this already?). :D

---

### Post by Merk42 on 2009-11-15
I guess either here or maybe [Ubuntu Brainstorm](http://brainstorm.ubuntu.com/)

But rather than submitting bugs and stuff to fix GRUB2 you'd rather take the time/energy to have GRUB1 be an option for Lucid?

---

### Post by ranch hand on 2009-11-15
Grub-legacy is no longer supported by the project.

I very seriously doubt that grub2 is going to hose your MS install.  The only part that touchs your install is os-prober and grub-legacy uses that too.

---

### Post by jocko on 2009-11-16
Instead of putting your energy into making the developers include a dead project in lucid, why don't you try to figure out exactly what went wrong with your install, try to fix it and post a bug report, so that the problem can be fixed?
In which way is your system "hosed"?
From the rest of your post I guess you mean that windows is broken, but in which way?

Does the grub boot menu have an option for windows, but it fails (with an error like "ntldr is missing")?
Then it's likely that grub is misconfigured and is looking for the windows boot loader in the wrong partition.
Or is there no option for booting windows?
Or does windows boot start normally but fail after a while?
In that case, did you by any chance resize the windows partition without defragmenting it (which sometimes leads to data loss)?

---

### Post by Gina on 2009-11-18
A few years ago I had a problem with Windows XP after re-sizing it's partition.  Two things you must do before re-sizing 1) defrag with hibernate and Windows swap turned off,  so that there are no un-movable flies (I had to do this several times before it moved the files down) and (2 make sure Windows is properly shut down before re-sizing - open files will definitely cause problems if you do anything with the Windows partition outside of Windows.

I hope you backed up all your important data before installing the new OS - that is ALWAYS recommended before doing anything to your partitions.

I am pretty certain your Windows problem is due to re-sizing you Windows partition - you've probably lost an essential file in Windows.

As above, if you tell us what is actually wrong with your Windows system we may be able to tell you how to recover it.  No guarantees, Windows really doesn't like being "messed with" from outside.  Otherwise, if you have an image of the Windows partition, you may have to restore that.  In the worst case, you may have to re-install Windows - but hopefully not.

P.S.  Although I've had some problems getting grub2 to install in the right place, my Windows system has not been touched in either of the two machines with Windows XP.  Also, grub2 correctly detected Windows XP and allowed booting it as before - no problem there.

---

### Post by pt123 on 2009-11-18
Brainstorm is useless, dead, a fad.

---

### Post by kansasnoob on 2009-11-19
Grub2 is here to stay. Work on making it better or learn to revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I don't doubt that there will be some "corner" circumstances where legacy grub will be the solution, but it's simply a matter of moving forward.

Hopefully we'll soon see some updates to grub2:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

---

### Post by kansasnoob on 2009-11-19
BTW there are still some "corner" circumstances where lilo works better than grub, so there will always be options available.

The options are greater using the alternate install CD.

---

### Post by Gina on 2009-11-19
Alternate CD worked for me (except for laptop - looking into that)  LiveCD refused to install grub2 on my two main desktops.  I'm going forward - I believe that's the way to go!

---

