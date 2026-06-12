---
title: "No caching mode page found - Stuck in some recovery loop"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2016-05-27
Hi Family.

I have been browsing the forum and googling for this problem and many folks have something quite similar but none of the solutions seemed appropriate.  So I'[m adding yet another plaint this problem to the pile.  (Hey, this ain't corporate; I can use the word "problem"! ;-)  )

I installed a fresh Ubuntu 16.04 a couple of weeks ago and it was never quite stable - often takes a few reboots (via GRUB) to get to the login screen.  But now I have a nasty issue and can't boot Ubuntu at all.  I get this set of messages, which I am copying by hand 'cause there's no way to capture the screen shot:
[FONT=Courier New][   3.027493] sd  8:0:0:0 [sdb] No caching mode page found
[   3.027542] sd  8:0:0:0 [sdb] Assuming drive cache write through
[   3.288588] sd 10:0:0:0 [sdg] Asking for cache data failed
[   3.288638] sd 10:0:0:0n [sdg] Assuming drive cache write through
/dev/sda5 Clean 238090/2101248 files 1606214/8388608 blocks
Welcome to emergency mode.  After logging in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "systemctl default" or ^D to
try again to boot into default mode[/FONT]

Hey, according to gparted I have three drives: 
[LIST]
[*]/dev/sda, my main hard drive, wherein /dev/sda5 is my Ubuntu boot partition, a member of an extended partition, /dev/sda4
[*]/dev/sdf, which is all NTFS, for my media and downloads
[*]/dev/sdh, a Corsair 8GB USB thumb drive
[/LIST]
I do not have drive sdb or sdg and I wish Ubuntu would stop worrying about them!  I believe that is at the heart of the problem.  But that's no reason not to throw in additional info that I have been able to salvage. :)

At one point I managed to get some kind of menu for diagnostics & maybe repair but I can't find my way back to that.

In any case, I was able to save the output of the journalctl command to a file - 1206 lines, about 101K.  Due to this forum's constraint on file size for attachments I was unable to attach such a large file so I split it in 7 files of 180 lines each.  But - another constraint - I cannot attach more than 5 files so I have xaa - xae attached here. If someone knows what to look for, they may be able to tell me what in blazes is happening.

I would prefer NOT to have to reinstall Ubuntu.  This is the first time an install didn't destroy my Windows boot partition.  (BTW, I have used a grub GUI to start Windows by default.)

<Sighh>  A quote from Mark Twain:  I didn't have time to write a short letter so I wrote a long one.

---

