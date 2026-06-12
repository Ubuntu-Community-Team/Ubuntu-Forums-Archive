---
title: "Cant dual boot along side windows 10. Any info appreciated."
date: 2015-08-30
forum: Installation &amp; Upgrades
---

### Post by ash18 on 2015-08-30
Unfortunately I am in need of Windows at this current point in time and I have just installed windows 10 as it runs faster than 7.
I cannot seem to dual boot Ubuntu to use as my primary OS. There just isn't the option in the installation. Only to erase windows and install Ubuntu.
I am assuming this is due to Windows Secure Boot. There's is no option to turn it off, as there was in W8.

What are the options here? Has anyone got around this with an easy process?

Any info would be much appreciated.

---

### Post by grahammechanical on 2015-08-30
Secure boot is not a Windows thing. It is part of the UEFI boot system. Does that motherboard have UEFI or BIOS boot system?

If the motherboard has a BIOS boot system then there is a 4 Primary partition linit for each hard disk. And if the installation of Windows 10 has used 4 primary partitions then the only option the Ubuntu installer can offer is to erase Windows and install Ubuntu. You could use a Windows utility to get a view of the partitions on the hard disk and then take a screenshot and post the image in your thread. In this way we will see what you are seeing and then give more accurate advice.

BIOS boot systems do not have secure boot. The fact that the Ubuntu live session can load and the installer can run shows that the problem is not secure boot related. Ubuntu has been crafted to handle secure boot since October 2010.

Regards.

---

### Post by ash18 on 2015-08-31
Thank you for the excellent information.

Attached is a screenshot of the all the drives. I have checked under system info and its Legacy not UEFI under bios mode.
I think from memory I can change it to UEFI in the bios setup, not one hundred on that.

So what next if its still bios? What is the next cause of it not being able to dual boot?

Appreciated.

---

### Post by oldfred on 2015-08-31
You are in BIOS boot mode & only have two partitions showing.
Was drive gpt and UEFI before?

Post this:
sudo parted -l

---

### Post by ash18 on 2015-08-31
No, it wasn't in that mode before when trying to dual boot.

Windows doesn't boot when I switch to UEFI.

Thanks

---

