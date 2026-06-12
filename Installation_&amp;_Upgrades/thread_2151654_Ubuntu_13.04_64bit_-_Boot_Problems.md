---
title: "Ubuntu 13.04 64bit - Boot Problems"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by Win8convert on 2013-06-05
I have just received a new Windows 8 PC which I am attempting to install Ubuntu on. the installation process when well, no errors or holdups. I selected the option for Ubuntu to erase and setup partitions as it saw fit.

When I reboot the machine it says "No boot disk has been detected".

I have disabled secure boot in the BIOS.

Can someone please help point me in the right direction?

---

### Post by grahammechanical on 2013-06-05
Is the internal hard disk listed in the EFI/BIOS boot system as having a boot priority?

We would get that message if the hard disk was not connected or if the hard disk had been formatted, removing the OS but not having another OS to replace the OS that had been removed. Run the live session and check to see if Ubuntu is actually installed onto the hard disk.

Regards.

---

### Post by Win8convert on 2013-06-05
> **grahammechanical said:**
> Is the internal hard disk listed in the EFI/BIOS boot system as having a boot priority?

We would get that message if the hard disk was not connected or if the hard disk had been formatted, removing the OS but not having another OS to replace the OS that had been removed. Run the live session and check to see if Ubuntu is actually installed onto the hard disk.

Regards.

The disk is internal.

I don't believe this is a disk problem as the drive is listed when I reboot into the live CD version of Ubuntu. When I attempt to reinstall Ubuntu it also detects the previous installation.

The drive is listed as the primary boot device.




I suspect it has to do with the deletion of the EFI partition.





.

---

### Post by Win8convert on 2013-06-05
Double post....

---

### Post by fantab on 2013-06-05
Boot from Ubuntu LiveDVD/USB, run the following command in the TERMINAL (Ctrl+Alt+T):

```
sudo parted -l
```

and post its output here.

---

### Post by Win8convert on 2013-06-05
Thanks for the responses but I managed to find a useful support document relating to _boot-repair_ :

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Option 2 sorted out the problem for me (Please mark this thread as SOLVED).

---

