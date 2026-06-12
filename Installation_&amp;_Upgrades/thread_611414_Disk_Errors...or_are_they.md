---
title: "Disk Errors...or are they?"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by Creepingdeadman on 2007-11-12
I've got two copies of 7.04, 32bit, and 64 bit, and also 7.10 32 and 64 now, and none of them will get past a simple disk error check.  A friend of mine used my 64bit 7.04 disk and it worked no problem. Here is a list of my components please respond if you have any ideas.

EVGA nForce 680i SLi SE Mainboard
Intel E6550 CPU
2x nVidia 7600GS's in SLi with a Readon x1300 in the middle for physics.
2GB OCZ Reaper Edition DDR2 800 Dual Channel Ram
Integrated Realtek Hi-Def Audio
2x Seagate 80GB Barracudas
2x Seagate 250GB Barracudas
HP dvd640 Disk drive


:confused::confused::confused:

Thank you for any responses.

---

### Post by Rmantingh on 2007-11-27
Unfortunately it is the case that some CD/DVD drives are better at reading a variety of disks than others.
Did you create the disks on the same drive that you're trying to read them from?
Usually that should work OK. It's often when you create disks on one drive and then try to read them on
another that the problems start.
Forgive me for asking the obvious but have you tried to clean either the disks by wiping them gently
with a soft cloth (from centre outwards only)? Or perhaps try a head cleaner to clean the lens?
How about the disk media itself? Is it a reliable brand. Is it worthwhile trying a different brand?
Sometimes buring the CD's again might help.
Otherwise do you have the possibility of swapping out a drive and replacing it with a borrowed one?
Not sure what else I can recommend.

---

### Post by Creepingdeadman on 2007-11-28
It's the same disk drive I was using in my old system in which i had a dual boot of Ubuntu 7.04 and WinXPPro, and on the same day I tried the disk, a friend of mine installed off of it, so I don't think it's the DVD drive.  I'm starting to think it might be my motherboard drivers not liking it, however EVGA says I should consult nVidia, and they just redirect me back to EVGA.

---

### Post by Rmantingh on 2007-11-28
A few more ideas to try:-
- Is there anything obvious to see in the BIOS? Is the drive 'auto' detected?
- Does it share an IDE controller with another device? Could there be a conflict?
- Are the jumper settings on the device correct? Master/Slave/Cable Select.
- If you have Windows installed as well can you confirm that the drive functions OK there?
   If yes, you could set up a virtual machine on Windows and try to install Ubuntu
   in there (and do a media check during installation).
- Try booting from a MS-DOS floppy and see if you can copy the CD to your hard-drive.
- Have you tried booting from a Live CD?
- Have you tried the 'Alternative' CD instead of the 'Desktop' version?
- It could be related to a memory fault ( [http://ubuntuforums.org/showthread.php?t=248628](http://ubuntuforums.org/showthread.php?t=248628) )
   Does the media check always fail at the same point (same file)?

---

