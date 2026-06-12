---
title: "error: invalid EFI file path."
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by Cyclops_ on 2012-09-18
Hi!

I just got a brand new ASUS laptop, and I'm trying to install a dual boot of Windows 7 and Ubuntu on it.  I'm using the latest Ubuntu download.

Since the laptop doesn't come with install CD's I have to use the special installer, which installs Windows to the entire hard drive.  I then use gPartEd to reduce the size of the installed partitions, leaving them in the same location, just smaller.  After this step, I can still successfully boot into Windows and use it.

Finally, I use the Ubuntu disc to install Ubuntu, being careful to specify my partitions, etc.
Once that install is done, I can easily boot into Ubuntu, but I get the following error when trying to boot into Windows: 

error: invalid EFI file path.

I've research the error, but I don't know anything about boot loaders and grub, etc.  In that area, I'm a n00b, so any and all help will be appreciated!!!!

Thanks!

---

### Post by dino99 on 2012-09-18
look at:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by oldfred on 2012-09-18
Did you use the 64 bit version of Ubuntu as that is the only one that supports UEFI.

You can use this to convert a BIOS install to UEFI, if otherwise ok. Or post link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Cyclops_ on 2012-09-18
I *did* use 64-bit Ubuntu.

I'll look over the links and see if I can figure this out!

Thanks guys!

---

### Post by Cyclops_ on 2012-09-18
That boot fixer tool seems to have done the trick.  Although, it named the new boot options funky names, and I wish I could clear out the old ones.

BUT... I'm not complaining!!!   (THANK YOU BOTH)

---

### Post by oldfred on 2012-09-18
Is the name issue from UEFI menu or from grub.

If UEFI, someone posted this, but every vendor is different on UEFI implementation.
Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

If from grub menu, you may be able to use grub customizer. Not 100% sure it works with UEFI.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by YannBuntu on 2012-09-18
Hello

> **Cyclops_ said:**
> That boot fixer tool seems to have done the trick.  Although, it named the new boot options funky names, and I wish I could clear out the old ones.

BUT... I'm not complaining!!!   (THANK YOU BOTH)

- Please indicate the URL provided by Boot-Repair (or create a new one [this way]("https://help.ubuntu.com/community/Boot-Info")).
- You can mark yourself as affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

---

