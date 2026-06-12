---
title: "Can't install Windows XP.  Already have Dapper installed."
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by rufusmcqueen on 2007-03-04
Hey helpful folks!

I recently installed Dapper on my old Sony Vaio PCG-FR130 after installing a new 120g HD.  I've gotten a (legal) copy of Windows XP and want to install it.  (I am new to Ubuntu and am leaving the country for a year.  As I'm much more familiar with Windows, I would do better to have it.)  I thought I could just pop the CD in and it would boot on powerup.  Imagine my surprise when that didn't happen.

I have read that I need to change the BIOS settings so that the computer reads the CD drive first.  How do I access the BIOS settings on my computer?  I have looked for a setup option on boot up, however all I see is a black screen that says only SONY.  Then, it begins to load grub.  Any help would be appreciated.  (Also, speak to me as if I were a child, please, as I'm not very proficient with computers.)  Thank you.

---

### Post by skale on 2007-03-04
With the Sony screen, try pulling up the "setup" or "settings" or "boot menu" or whatever it is called (F12 for me, but I have a Dell).  When there, look for something to do with boot order, and make the CD before the hard drive.  Be sure to change it back, for security purposes.  

Before you install Windows, make sure you have set up a partition for it, of type FAT or NTFS.  It's best to do this from the linux side, and then format it with the Windows CD.  And, windows overwrites the MBR with its own bootloader, which only boots (surprise) windows.  To be able to boot Ubuntu, make sure you install GRUB again, from the Ubuntu alternate CD.

Good Luck

---

### Post by rufusmcqueen on 2007-03-05
Okay, I got into the BIOS screen and changed the boot order.  However, it still did not boot the Windows XP disc.  Do I need to go ahead and partition the hard drive?  Do I need some type of boot diskette for Windows?

---

### Post by rufusmcqueen on 2007-03-05
Any help out there?

---

