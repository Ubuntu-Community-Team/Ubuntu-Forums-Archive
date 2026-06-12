---
title: "Cannot install 64 bit v9.10 or 32 bit v10.10"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by 10-78 on 2010-11-26
Hi, I'm a novice on Ubuntu.

    I have an MSI 785GTM-E45  mobo with an Athlon 64 CPU.  I previously had Ubuntu v9.10 installed via CD and verified with MD5SUM on this PC.  After installing a different HDD I cannot install v9.10 with the same CD.  After reaching the "Install Ubuntu" screen I get the following message no matter which choice I pick from the menu:

    BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
    Enter 'help' for a list of built-in commands.
    (initramfs) Unable to find a medium containing a live file system

    Then I downloaded 32 bit v10.10, burned it to a CD and verified it with MD5SUM.  After seeing the Ubuntu logo with scrolling dots, I get the following message:

    BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built in shell (ash)
    Enter 'help' for a list of built-in commands.
    (initramfs) Unable to find a medium containing a live file system

    I've installed another HDD and gotten the same results.  Both HDD's have been partitioned and formatted.

    I've been through over thirty pages of threads and found discussions involving similar error messages but no solutions other than one guy whose HDD was shot.

HELP!  ](*,)

---

### Post by 10-78 on 2010-11-28
Just for the hell of it I downloaded and installed ISORecorder and burned a DVD of v10.10 at the slowest speed.  No difference, I get the same error message.

I'm getting more disappointed in this "help" forum day by day.  Where's the help?

---

### Post by ryegras on 2011-03-16
I have exactly the same problem with Ubuntu 10.10 x64 and after trying both DVD/CD drives, PATA and SATA connections, changing from AHCI  to IDE in the bios, re-burning the disk etc., and Googling the problem, I can not get Ubuntu to load in any form. Since I am a long time Windows user and fed-up with all the user unfriendly features of Windows 7, I thought I would give Ubuntu a try but the very fact that their install disk will not load leads me to believe that this version is 'not ready for prime time'.

 BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

---

### Post by djDorkins on 2011-03-16
> **ryegras said:**
> this version is 'not ready for prime time'.

Although I don't have an answer to your problem (I've never had an issue with installing *any* Linux distribution), I invite you to read this, albeit rather lengthy, article:
[http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

By the way, have you tried installing Ubuntu from a memory stick?

---

### Post by Hakunka-Matata on 2011-03-16
Are you able to select the "Try Ubuntu without installing" option?

---

### Post by targets on 2011-03-16
same here i just cannot get 10.10 to load up on  a variety of PCs with different configurations .the PCS are not old, last years models so the BIOSs are recent .
tried using a CD and a USB stick ,intel and AMD mobos .
sata  and ide disks which were formatted and given the run of the disk for the install

---

### Post by Hakunka-Matata on 2011-03-16
Welcome, please explain more precisely the mode of failure[LIST]
[*]Computer will not boot from CD
[*]Computer will not boot from USB
[*]Ubuntu install LiveCD/USB starts computer but fails during the attempted installation or Try Ubuntu phase?
[/LIST]

---

### Post by 10-78 on 2011-03-16
To put this one to rest, I finally determined that the problem was with the motherboard and NOT Ubuntu.
Thanx to those that tried to help.

---

### Post by Hakunka-Matata on 2011-03-16
OK, good.  Would you mind marking your thread [SOLVED] ?

top of page, right hand side,[COLOR=Red]_Thread Tools_[/COLOR], thanks

---

### Post by ryegras on 2011-03-17
Yes, I totally understand that Linux /Ubuntu is not Windows however I at least expected to get to some kind of an operational state before having to search/tweak. Not being familiar with Ubuntu, it may well be a driver or other hardware related issue since I too am trying to load it on a brand new machine (Asus P8P67 with an Intel 2600K). It's not as though the CD isn't trying to make a valiant effort before the BusyBox and initramf errors as I get a beautiful Ubuntu purple screen (with a little stick figure of a man at the bottom ;-)) as portions of the CD are loaded it to memory and then:

 BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system


with no further options for install or running the program from the CD.
Thanks, Randy



P.S. Problems seem to be after program is in memory and not necessarily due to CD versus USB stick (friend's computer with different hardware had same installation problem). Oh, also these drives are on the good IDE/SATA ports on this board, not the ones Intel had problems with.

---

### Post by mörgæs on 2011-03-17
'Keyboard-man' means 'push any key'. If you do this, you will get to a menu, where you can test the CD for defects. How does this come out?

---

### Post by Hakunka-Matata on 2011-03-17
> Post #8: from 10-78

To put this one to rest, I finally determined that the problem was with the motherboard and NOT Ubuntu.
Thanx to those that tried to help.10-78 What was your "Motherboard problem" ?  


There are several different people posting the problem here, gets a bit confusing who's who.


[LIST]
[*]ryegras
[*]djDorkins
[*]targets
[/LIST]
Are you all working with the same motherboard?  Is the problem a BIOS setting?  Do  you have SATA controller mode set to "AHCI"?

---

### Post by djDorkins on 2011-03-17
> **Hakunka-Matata said:**
> 
[LIST]
[*]djDorkins
[/LIST]

I'm not having any issues. ;) My first thought is that it could be a RAM/motherboard issue.

---

### Post by targets on 2011-03-17
its both ASUS mobos with AMD and *INTEL cpus ,bought last year . is ubuntu MOBO picky?*

---

### Post by Hakunka-Matata on 2011-03-17
see post #8  10-78

---

### Post by banifou on 2011-07-21
I've the same problem, for the first time at installing Linux! 
Did anybody solve the problem.  I'm stack.

What was the issue with the motherboard?

Thanks in advance

---

### Post by mörgæs on 2011-07-22
Which problem exactly do you have? 
Which Ubuntu releases have you tried?
On which hardware?

---

### Post by dcastor on 2011-07-28
I had the same symptom - BusyBox error saying essentially that it was unable to find a live filesystem.  And, I found the solution in another thread, folks changed CD-ROM SATA mode from IDE to AHCI.  It worked great for me too.

---

