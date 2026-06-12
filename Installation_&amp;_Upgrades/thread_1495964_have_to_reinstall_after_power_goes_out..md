---
title: "have to reinstall after power goes out."
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by harmsc12 on 2010-05-28
My computer is always having problems.  The newest one is that after I turn off my computer completely and then turn it back on again, it acts like there's no OS installed and prompts me for a system disk.  Any fixes or even an explanation why would help.

---

### Post by WinRiddance on 2010-05-28
> **harmsc12 said:**
> My computer is always having problems.  The newest one is that after I turn off my computer completely and then turn it back on again, it acts like there's no OS installed and prompts me for a system disk.  Any fixes or even an explanation why would help.
[B]
Boy, so many possible symptoms, where to begin ....[/B]
Would have been nice to know the age of the machine, how much Ram, type of processor and speed, as well as how long these problems have been going on ???

_The two biggest causes_ for weird startup symptoms are excessive heat (the cpu working too hard in an excessively warm environment) and dirt within the system which causes the interior of the system to overheat - or fans to clog - thereby causing the cpu often to overheat as well. Lousy graphic cards can wreak havoc on a machine, as can incompatible Ram modules. I'd consider those as causes 3 and 4 for weird startup behavior. Believe it or not, but some older modem and/or DSL/ethernet cards used to cause erratic startup behavior too.

**If you have an older machine** that's prompting you for a disk, it's possible that the bios has been set to boot from a CD (required when using an Ubuntu LiveCD). Well, some older bios settings **don't** automatically revert back to looking for a hard disk boot option and if you have a system like that it may tell you indefinitely that it can't find a disk ... if you don't have a bootable disk in your CDRom drive or until you change the boot sequence back to what it was before (booting from hard disk one). If your computer works **with** a LiveCD in the drive then that may well be part of your problem.

To prevent overheating keep your fans clean. Leave enough space around the computer for it to be able to "breathe" properly and take it out of the darn cabinet if it's sitting inside one of those ridiculous wooden desk enclosures with a door. Believe it or not, the worst kind of crud that can mess up a computer fan is nicotine. Seen CPU fans gunked up so bad, took the CPU and mainboard out at the same time. I've rebuilt computers from smokers where the finest, heaviest, and stickiest dirt was nicotine dust from years of smoke being sucked into the system by the fans. Incredibly disgusting. There's a reason why big corporations keep their systems in a perfectly clean, air conditioned environment .... 

**If you have an older SCSI drive** on your system it might be going bad. That would be accompanied with a constant whining sound though. Your mainboard could be biting the dust. One of your ram modules or drive connectors could be loose. Like I said, the range of symptoms for what you're describing is virtually endless. Perhaps this answer might be able to help you? Good luck ....

---

### Post by efflandt on 2010-05-29
Are you properly powering your computer down from Linux, or are you just hitting the switch to turn off your computer?  Whether running Windows or Linux, you should have the operating system shut it down, so any delayed writes to the hard drive take place before the power goes off.  And you certainly should not manually power it off while writing to disk.  For that reason, it is also a good idea to have your PC on a UPS (uninterruptible power supply).

Unless your computer is so old that it does not have power management, or that is not working in Linux, you could go to System > Preferences > Power Management and in the General tab set **When the power button is pressed: Shutdown**.

Maybe your drive is jumpered as slave, instead of master or cable select, or if more than one drive, they are both jumpered as master.  I once bought an open box (returned) PC for $100 that would not boot at all until all of its other drives were unplugged.  Once I sorted out the drive jumpers and cables everything worked, including its cdrom and LS120 Super Disk.

I do have a strange issue with an old laptop (Compaq V2000).  If I shut it down for a short period of time, it starts booting immediately when I hit the power button.  But if it has been off for a while, it will not power up at all, no matter how long I hold the button, until I remove all power from it (including disconnecting AC and/or removing its battery).  After that it starts right up.  I wonder if its CMOS battery is bad (for BIOS settings and clock/calendar)?

---

