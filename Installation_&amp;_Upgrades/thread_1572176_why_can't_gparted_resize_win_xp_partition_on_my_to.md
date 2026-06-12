---
title: "why can't gparted resize win xp partition on my toshiba laptop?"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by chaparrazo on 2010-09-10
i'm trying to do a dual boot win xp and lucid on a toshiba satelite a105 laptop i just got on cl. it came with a fresh install of win xp pro. so i do my research and read that you boot from the live cd and then do gparted to adjust the partition to open some space for ubuntu. sounds cool so far. 

i get to the manual partition screen where you type in the new size and it won't take a new number. i hit tab and it jumps right back to the original size. i can move the partition about 8 gigs either direction (before or after where it's currently at) but cannot get it to change the size of the partition itself. 

any ideas? 

thanks!

---

### Post by wilee-nilee on 2010-09-10
Take a screenshot of gparted.

---

### Post by chaparrazo on 2010-09-10
here ya go

---

### Post by oldfred on 2010-09-10
If you right click on the triangle with the exclamation point does it tell you anything. Often gparted and ubuntu will not recognize a NTFS partition that requires chkdsk or is hibernating.

The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

### Post by wilee-nilee on 2010-09-10
> **oldfred said:**
> If you right click on the triangle with the exclamation point does it tell you anything. Often gparted and ubuntu will not recognize a NTFS partition that requires chkdsk or is hibernating.

The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

+1 this happened to me last week, with W7, the chkdsk was suggested and fixed the problem.

---

### Post by chaparrazo on 2010-09-10
i get a "command not found" as a response. is this not included on the live cd maybe?

this is a command i'm sposed to try in terminal, right? 

duh? scratch that - i sposed to do it in xp . . . . ok let's give it a shot. 

thanks all for your help. just a sec . . .

---

### Post by efflandt on 2010-09-10
Besides some issue with Win XP that makes gparted not want to touch it until Windows fixes it, you may have files that cannot be moved and might be near the end of the partition, usually virtual memory (similar to a Windows swap file).  So you should boot XP and find System, Advanced tab, make a note of current virtual memory size and disable it.

You have to reboot for that to take effect, so you may also set XP to check your C: drive which it will do the next time it boots.

After you shrink Windows, gparted will mark it as dirty so it will be checked again when Windows reboots after that (to make sure the resizing was successfull).  Any time after your ntfs partition  has been resized, you can re-enable virtual memory in Windows.

Other than that, everything on my A105-S4384 worked in Ubuntu without any issues or special drivers.  Although, other A105 models may have different hardware.

---

### Post by chaparrazo on 2010-09-10
thank you thank you thank you. just resized and going back to install!!!

---

