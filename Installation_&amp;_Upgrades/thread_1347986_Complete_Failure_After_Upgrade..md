---
title: "Complete Failure After Upgrade."
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Dorrax on 2009-12-06
I was using ubuntu 9.04 and started to experiment with installing ubuntu on USB drives. But the other day I decided I wanted my flash drive back as a flash drive so I tried to delete the files. The files wouldn't delete normally so I went into terminal, and used sudo rm and rm dir to get rid of the files. I got tired of one file at a time though and used some command like sudo rm /media/disk/bin/* or something. Anyway, I think the wildcard screwed me over and got rid of some files on my hard drive instead of the flash drive. This caused a kernal panic after selecting my OS on grub. So I used one of the USB drives with linux to boot up and mount the bad linux partition. I followed the instructions here: [This link]("http://ubuntuforums.org/showthread.php?t=35087&highlight=system+backup"), to back up my /home folder onto my external HD. Then I installed xubuntu 9.10 32 bit over the bad ubuntu partition. Things seemed to work ok at first, installed fine, booted up fine. But the next time I booted up the computer, the mouse didn't work. When the cursor was over an icon, the icon lit up, but the arrow didn't appear until I forced the screen to refresh by changing the resolution. But the arrow wouldn't move until I forced another resolution change. So I turned it off and came back today only to discover that I have a low graphics mode error similar to here: [HERE]("http://ubuntuforums.org/showthread.php?t=1347237&highlight=backup+restore"). I am being forced to use my windows dual boot while I figure out how to fix this. Not sure the windows is working well though, I keep getting notices telling me that chrome.exe is corrupt and I need to run a disk check.

To further frustrate me, the backup file I made won't work. I get an "unexpected EOF error" or something like that. I had important files on there I would like to get back...

So far it seems I'm not the only one with the low graphics problem, but the backup problems are like sticking a knife in my eye and twisting it.

---

### Post by quixote on 2009-12-07
Yikes.  Bad news. :(

I'd say that the first thing is to get a working ubuntu partition back -- and don't do anything to your /home backup.  Recovery is generally easier the fewer disk accesses there have been.

The ubuntu (well, xubuntu) partition sounds like it has free-floating issues that are very hard to troubleshoot.  I hate to say it, but if it was me, I'd just do a reformat and reinstall.  Maybe somebody else has some ideas on how to troubleshoot?

Once you have a stable install, then check your backed up /home again.  It's just possible the errors are being caused by the wonky install and aren't really there.  We can hope anyway.  If they're real, then it's on to seeing how much [testdisk]("http://www.howtoforge.com/data_recovery_with_testdisk") can do for you.  (More helpful info [here]("http://ubuntuforums.org/showthread.php?p=8229282") and [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").)

---

