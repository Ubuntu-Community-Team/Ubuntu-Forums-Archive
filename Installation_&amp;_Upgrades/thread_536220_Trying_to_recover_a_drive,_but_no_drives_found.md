---
title: "Trying to recover a drive, but no drives found"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by rillip on 2007-08-27
So here's the situation:

I had win2k on a 40g pata.  There was an 80gig sata that acted up, sometimes it showed up, sometimes it didn't. Figure it was the raid drivers or bios, didn't really have time to look into it and didn't need it yet anyway.

I scored a new mobo/ram/processor from a friend and decided I'd get the sata working on it, install xp, and then migrate my data from the 40g pata.

The sata worked without issue in the new mobo, so I'm guessing it was bios.  I plugged in te 40g pata, booted, everything was good.  Set my files up to copy and started doing other things.

I came back to see the progress, only to find the directory listing had crashed. I tried to close it, it would ask me if I wanted to end it now, I'd tell it yes, it never would.  I tried killing explorer.exe (this used to work in 2k) but in XP apparently it never comes back, as I just sat there with my open windows and no way to get a task bar or desktop back.  

I log off and log back in.  It tells me that it was unable to write the file D:\.hlskdj34 (some more random charachters trailing off).  Now I go to copy my files again, and it tells me the folders aren't accessible, they're corrupt or unreadable.

I reboot, get in fine, start copying agian, part way through it aborts, telling me the files are corrupt or unreadable.  I reboot, again, and it wants me to run chkdsk.  Hit any key to cancel. Well, I hit some keys and it doesn't let me.  Whatever.

So it runs for about 1 second and comes back with "master file table corrupt, abandoning."

... GREEEEEAAAAT.

I tried running fixboot from the recovery console after reading about it and then tried chkdsk again, but no luck, same error.  I tried some recovery software, it finds the files, but then when it's time to pick files to recover, it says it can't find the file system, sorry, pick a new partition.

I thought I'd give Linux a shot at it, see if maybe I could mount it and pull some files off, or maybe there would be some better utilities for this.  I pop in my LiveCD for 6.06 and get "the timer isn't connected to the... " blah blah error.  I recognize it and turn off acpi by adding "noacpi acpi=off" to the boot options. It boots now, but no drives are detected, neither my good sata or my bad pata.

Any suggestions?

---

### Post by Pumalite on 2007-08-27
Use Gparted: (the stand alone-burn-to-CD-bootable-program):
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
See if it sees both your har drives. Post back.
Also use: rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Investigate your system and report back.

---

### Post by rillip on 2007-08-30
gparted showed the drives, but there wasn't a whole lot I could do from that point, since I don't want to format.

Rescue CD found both drives, but when I try to mount the fautly drive, it gives me a invalid MFT error as well, and recommends I run chkdsk /f and reboot to Windows twice.  If I run chkdsk /f it immediately returns "corrupt mft, aborting" and doesn't do anything.

Any other ideas? :/

---

### Post by merlinus on 2007-08-30
You might try this:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It may be on the rescue cd as well.

-merlin

---

