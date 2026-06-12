---
title: "Software Raid 1 Fiesty Fawn Installation Troubles."
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by undump my core on 2007-04-14
I've spent the last two days trying to get Feisty Fawn (7.04) installed with raid 1.   I've got a new machine with 2 identical SATA drives.  It seems doable.   But maybe my Ubuntu mojo isn't good enough.  

I've been using the Kubuntu flavor.   First I tried the regular installer.   I was able to convert the /home partition to raid.   But I couldn't figure out how to convert the root partition.  It's possible I might have been able to do it with LILO.   But I could make enough sense out of GRUB.  I could have created another degraded raid array with mdadm.  Perhaps I could have copied the root directory to it.  But I didn't have a clue as to how to make it boot.   

So I decided to try the alternate installer.  Perhaps this was a bad idea.  I changed the root and home partitions to raid.  Then the alternate installer freaks out and can't read the disk at all.  It seems that maybe the alternate installer can create raid partitions; But it can't understand them.  

Has anyone had any luck getting raid 1 setup?  If so, how did you do it?  Right now I'm thinking that maybe it can't be done with the alternate installer.  Is this right?  Also, I'm thinking that it could, in theory be done after installation, but maybe this isn't so easy. 

Interestingly, in the alternate installer I get an error message that says "Could not stat device /dev/md/1 - no such file or directory"  However, when I execute a shell I find that mdadm is alive and well and /dev/md1 is clean, degraded, and recovering.  Yes, the percentage keeps increasing.  Also,  /dev/md2 is active.   Should I just continue to wait in the hopes that when the rebuild completes the installer error will go away?

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

