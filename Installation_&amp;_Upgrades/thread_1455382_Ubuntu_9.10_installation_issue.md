---
title: "Ubuntu 9.10 installation issue"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by tomray on 2010-04-15
Greetings, all:

I have installed 9.10 several times with great success for a particular application I'm running.  But I have two computers with a strange problem.

Brand new 2TB drive - fresh from the box.  Nothing on it.  I boot up the live CD, then tell it to install Ubuntu.  We go thru the usual stuff, then it proceeds to start formatting and installing the system.  It faults out on fully installing grub.  On restart, I get a ton of "bad sector" messages.  The system will not reboot; I can boot to the live CD, then select "boot from hard disk" and it will boot up - but I can't install grub - and it places an install icon on the desktop.

It's not an issue with the drive.  I got the same bad sector messages - listing the same exact sector numbers - on a known good 80GB drive.  

For fun, I tried installing Windows XP on the 2TB drive.  Installation happened just fine - no issues at all.  So, I then decided to try a dual boot install of Ubuntu.  Same bad sector messages, and the system simply boots to Windows.

I've seen this on another computer - different brand.  I'm thinking it may be some issue with the drive controller, but today's computer is using a SATA drive - the previous computer where I encountered this was EIDE.  This computer has a brother, same brand, slightly different model using a 1.5TB SATA drive that installed just fine.  I'm also wondering if it might be something with the CD ROM settings.  Or something in the BIOS (though my bios options are somewhat limited on this machine).

Any thoughts?

Tom Ray

---

