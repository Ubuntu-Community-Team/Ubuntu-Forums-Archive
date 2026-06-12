---
title: "Dual booting with 2 hdds question"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by Mendel314 on 2013-09-04
I have a new laptop in the mail, a clevo p375sm.  I have windows already installed on the ssd.  This laptop supports several hard drives, and I really want ubuntu on one of them for a dual boot.  I want to install 13.04 onto the momentus xt i have in my current computer, then just plop that hdd into the empty drive slot on my new computer, then configure the bios to ask which to boot into.  Do you think, given that the new computer has radically different hardware than the one I want to do the install on, there will be issues? Or should I just wait until the new computer arrives, install the xt, and do a clean install to it from the clevo.  

I guess what I need to know is if the drivers will auto update or if there's a simple command I can enter to get the up to date ones, after installing ubuntu with a far inferior machine.

---

### Post by grahammechanical on 2013-09-04
> Do you think, given that the new computer has radically different  hardware than the one I want to do the install on, there will be issues?

What do you think? Different hardware? What version of Windows? Version 8? Does your present computer have secure boot? A Windows 8 machine will have secure boot. Install Ubuntu on a machine without secure boot and then put the hard disk into a machine with secure boot and it is likely that the OS will be rejected as failing secure boot requirements.

It is best to wait and then if you install Ubuntu 13.04 on the machine with secure boot Ubuntu will provide a Linux kernel that is acceptable to the Microsoft secure boot requirements. But first check the forum for all those posts from people who have had and are having problems installing Ubuntu alongside Windows 8.

Regards.

---

### Post by Mendel314 on 2013-09-04
It's windows 7.  I'm going to be using the computer for a CAD class, and solidworks has better support on windows 7.  I take it that I should wait then...

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2013-09-04
Some computers that support two drives by swapping CD/DVD for a hard drive will not boot from that hard drive. You need to check manual or instructions to see if it will boot from second drive. 

To easily dual boot.
If Windows is BIOS/MBR you need to install Ubuntu in BIOS mode also but can use gpt partitioning if drive will be Linux only. Windows only boots from gpt drives with UEFI.
If Windows is UEFI you need to install Ubuntu in UEFI mode.
Most new computers are really UEFI, but have CSM -         UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
So you have to pay attention to how you boot Ubuntu installer as it will offer both choices if a UEFI system. And how you boot installer is how it installs.

---

