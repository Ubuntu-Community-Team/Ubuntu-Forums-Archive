---
title: "Ubuntu 21.10 installer not finding HDD"
date: 2021-10-16
forum: Installation &amp; Upgrades
---

### Post by mikeyharris2 on 2021-10-16
Hey,
My Acer Aspire has a 500gb SSD with Windows and a 2tb HDD full of music. I want to dual boot but the Ubuntu installer will only see the 2tb. Any ideas on how to choose drives?

---

### Post by MAFoElffen on 2021-10-16
More information needed...
Which model of Acer Aspire?
If you boot the installer to the "Try" Mode, does it run stably? If in the LiveCD environment does the system see the drive?

If not sure of the hardware details, you could run the UbuntuForums system-info script in my signature line to provide most of those and other needed details in an automated fashion (from the Installer LiveCD).. or I could walk you through typing the commands in a terminal session and posting some needed information in posts manually... Your choice.

---

### Post by mikeyharris2 on 2021-10-16
Hi, Its an Aspire z3-715. 16gb ram ,Intel(R) Core(TM) i5-7400T.  The live boot doesn't show the 500gb SSD that Windows is on. Just the 2tb HDD

---

### Post by oldfred on 2021-10-16
Slightly newer model, should otherwise be similar:
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

Many Acer need UEFI update and SSD firmware update.
Drive needs to be in AHCI mode. 
Windows fast start up needs to be off.

UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)

Also general install instructions in link in my signature.

---

