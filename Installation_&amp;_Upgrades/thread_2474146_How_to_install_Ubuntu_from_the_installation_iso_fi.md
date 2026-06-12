---
title: "How to install Ubuntu from the installation iso file using dd command?"
date: 2022-04-22
forum: Installation &amp; Upgrades
---

### Post by accountownernumberten on 2022-04-22
I downloaded the latest Ubuntu installation media which is a ".iso" file. It booted and began to install Ubuntu but I got an error number ten. I want to try one more time but using the dd command. But the file that I have is the installation ".iso" file. Should I somehow extract it or something before using dd?

---

### Post by TheFu on 2022-04-22
I don't think Ubuntu install via 'dd' will get you what you seek.

You can use dd, cp, cat, ddrescue, mkusb, ventoy, yumi, and a bunch of other tools to perform a bit-for-bit copy of the ISO onto either flash USB, SDHC storage.  All of these are destructive. Assume they wipe any existing files, though that isn't always the situation. Those tools create an install-able media, which should be bootable and can be used for either an installation OR in a *Try Ubuntu* mode.  It is also very handy to have one of these flash drives to fix and troubleshoot Linux issues that cannot be fixed while booted on the installed OS (on a HDD/SSD).

What is it that you are trying to accomplish?  I hope if you have the .ISO file, then your goal is to create installation media, since that's what it is for.

BTW, I haven't looked at 22.04, but with 20.04, there was a built-in checksum capability with the ISO to validate that the media contained the correct bits as expected from the ISO.

I've been an admin and user for 25 yrs and I don't know now to 'install Ubuntu' using dd, so perhaps that really isn't what you seek?  Sometimes we may seem pedantic here, but using the correct terms for specific needs is important. It prevents misunderstandings and hopefully, it will prevent someone from misreading, then wiping their system, unless that is their goal.

---

### Post by GhX6GZMB on 2022-04-22
I think the OP is under the impression that installing Ubuntu is like installing a program package. It's not.
Ubuntu needs to be booted to start the install.
The two main options are:
1: burn a DVD with the .iso and boot from there.
2: create a bootable USB thumb drive with the .iso and boot from there.

Cheers.

---

### Post by TheFu on 2022-04-22
Good idea, ml9104.  I was thrown off by "It booted and began to install Ubuntu but I got an error number ten."  
Ubuntu is a full OS. No other OS loads it as a program.

If you have a Unix-like OS, then you can perform a bit-for-bit copy of the ISO file onto a storage drive/device like a thumb drive or SDHC card, then boot from that.  That's what dd can do, but you'll need to be extremely careful to get the correct target device name 100% correct.  Get it wrong and it is very likely to wipe any other OS or data partition/drive on the system.  Just seems to work out that way.  OTOH, with a full understanding of Linux device names, dd is one of the fastest ways to create a bootable, installable, flash device from an ISO.  If you aren't 100% certain, please use a different tool that has validation checks and warnings to prevent selecting the wrong target storage.  Please.

---

