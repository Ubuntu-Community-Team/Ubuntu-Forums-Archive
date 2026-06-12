---
title: "Windows 7 does not load(sometimes) after installing ubuntu."
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by the most naive user on 2011-10-27
Windows 7 does not load(sometimes) after installing ubuntu.

I had a system with windows 7 installed.
I installed ubuntu 11.04 alongside windows.
The installer created another partition for ubuntu.

The problem is:
ubuntu loads perfectly fine.
Windows loads sometimes , sometimes the system restarts on the windows loading screen. I think it has something to do with ubuntu.
If windows loads and i continue to use windows , it will load everytime , but if I use ubuntu in between windows will not load for couple of times. Sometimes windows does not load at all.

I don't know anything about linux.
O/P of sudo fdisk is :
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS/exFAT
/dev/sda2        81915902   312580095   115332097    f  W95 Ext'd (LBA)
/dev/sda5        81915904   163827711    40955904    7  HPFS/NTFS/exFAT
/dev/sda6       163830933   245746304    40957686    7  HPFS/NTFS/exFAT
/dev/sda7       245746368   294579461    24416547    7  HPFS/NTFS/exFAT
/dev/sda8       294580224   308916223     7168000   83  Linux
/dev/sda9       308918272   312580095     1830912   82  Linux swap / Solaris

I think this is a known issue. Someone else had also posted about it. I think windows and ubuntu interfere with each other. 

Thanks & Regards,
Rachit P

---

### Post by ahso4271 on 2011-10-27
ive installled win8 dev prev without problems. only vista and win8 i had to tell the default os. 
maybe do a fixmbr from windows? or use:

[http://blog.tim-bormann.de/anleitung-windows-8-deinstallieren.html](http://blog.tim-bormann.de/anleitung-windows-8-deinstallieren.html)

ev. try with google translate from german.

---

### Post by Mark Phelps on 2011-10-27
Don't mess with your MBR.  That has nothing to do with the problem.

Next time you boot into Win7, run a CHKDSK on your OS partition.  To do this, click on Computer in the Start area.  This should show a list of partitions (Win7 will call them Hard Drivers).  Right-click the OS drive and select Properties.  Then, select the Tools tab, then click the Error Checking button.  You will have to reboot into Windows for this to take effect.

Also, are you writing to your Windows partitions from inside Ubuntu? Or, are you mounting your Win7 OS partition read/write?  If so, those could be causing the problem.  It's best NOT to mess with Win7 OS partitions from inside Ubuntu.

---

### Post by the most naive user on 2011-10-27
Also, are you writing to your Windows partitions from inside Ubuntu? Or, are you mounting your Win7 OS partition read/write? If so, those could be causing the problem. It's best NOT to mess with Win7 OS partitions from inside Ubuntu. 

------
I mount windows partitions , but not the one in which windows is installed (Which is C:/ on most windows system and mine too)

---

### Post by oldfred on 2011-10-27
Do you hibernate? Even if not writing into c:, if you hibernate and have a file in use from d: or e: and then do something in Ubuntu it can interfere with the hiberfile.

---

### Post by the most naive user on 2011-10-28
No i do not hibernate ..i shutdown ubuntu.
Right now i am working from windows. I had to try three times to boot into windows.

---

### Post by oldfred on 2011-10-28
I meant hibernate in Windows. 

Does it make a difference if you warm boot or cold boot (full shut down and then restart after 10 seconds or so)?

---

### Post by the most naive user on 2011-10-28
no i always shutdown ..( full shutdown) in both ubuntu and windows.

---

