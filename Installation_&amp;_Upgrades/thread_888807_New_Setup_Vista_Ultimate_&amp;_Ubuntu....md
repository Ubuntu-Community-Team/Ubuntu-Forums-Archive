---
title: "New Setup: Vista Ultimate &amp; Ubuntu..."
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by Luf on 2008-08-13
Heya,

First off, I would like to state that I'm rather new to the Linux scene, although I am adept to computer technology and other OSs. So thanks for your patience...

I have a home built machine. I am looking to install Vista Ultimate x64 and Ubuntu 8.04. I'm not sure if this is a better method than partitioning, but I would prefer to have them on separate HDs. My question is:  **"What do I need to do as far as bootloaders are concerned?"**. Last I heard, GRUB didn't 'understand' the Vista MBR or the new NTFS set. Are they playing nice now? What do I need to do to get this working?

thanks in advance!
~Luf.

---

### Post by logos34 on 2008-08-13
read this:
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20boot%20record%20and%20boot%20manager](https://help.ubuntu.com/community/WindowsDualBoot#Master%20boot%20record%20and%20boot%20manager)

Try using grub to dual boot. If it doesn't work, restore the windos bootloader from the vista dvd repair environment.  Then get EasyBCD.

good luck

---

### Post by Luf on 2008-08-13
> **logos34 said:**
> read this:
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20boot%20record%20and%20boot%20manager](https://help.ubuntu.com/community/WindowsDualBoot#Master%20boot%20record%20and%20boot%20manager)

Try using grub to dual boot. If it doesn't work, restore the windos bootloader from the vista dvd repair environment.  Then get EasyBCD.

good luck

Alright.

Should I install GRUB on the HD Ubuntu will be on, or should I use the GRUB for Windows I've been hearing about? Not too sure how to attack this with 2 SATA drives.

thanks,
~Luf.

---

### Post by logos34 on 2008-08-13
Install vista first.

Then, since you have two drives, you could make sure grub installs to the MBR of the ubuntu drive, leaving the vista bootloader untouched on the other disk.  Here's how:

-go into the Bios and switch the ubuntu drive to first postition in the hard disk boot order.
-boot the ubuntu live cd and begin the installation. Note the drive designation of the ubuntu disk (sda or sdb).  When you come to 'Ready to Install' screen (step 7 I believe), press the 'Advanced' button and replace the default Grub bootloader location of '(hd0)' with /dev/sda, or whatever the ubuntu disk is.  Now there is no way grub will overwrite the windows bootloader, AND you won't have to edit /boot/grub/menu.lst to get it boot correctly.  Ubuntu should detect windows on the other drive and add the appropriate boot entry.

So basically you'll be booting from the ubuntu rather than vista drive, and your grub menu screen will give you the option of Vista on the other disk (the latter's menu.lst entry should have 'map' lines).  

This is a nice arrangement since if you ever have problems with either OS, you can always boot the other via the Bios because they are completely independant

---

### Post by Luf on 2008-08-13
Perfect.

I think that covers everything. ^_^

Thanks for the quick reply!

~Luf.

---

