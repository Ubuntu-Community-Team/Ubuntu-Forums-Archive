---
title: "Need to uninstall"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Virtua-Touch on 2008-11-09
I am running a Win98/Ubuntu 8.04 Dual boot and I need to uninstall. Can anyone help me out here?

---

### Post by bulldog on 2008-11-09
Which one do you prefer to un-install?
If you want to get ubuntu out of your system,just format the partitions with windows NTFS file system.
If GRUB is installed in the MBR,you need to recover the windows MBR,you can do that with the windows install cd and recovery option,choose fixmbr or/and fixboot and GRUB will be gone.

I assume you didn't use WUBI installer?

---

### Post by billgujie on 2008-11-09
> **bulldog said:**
> Which one do you prefer to un-install?
If you want to get ubuntu out of your system,just format the partitions with windows NTFS file system.
If GRUB is installed in the MBR,you need to recover the windows MBR,you can do that with the windows install cd and recovery option,choose fixmbr or/and fixboot and GRUB will be gone.

I assume you didn't use WUBI installer?
hi,

saying if i need recover the windows MBR, do i format the linux partitions first then use windows install cd to perform recovery?

Because i tried to boot the windows install cd when both of two OS are on my computer it failed to boot, i guess its because the GRUB not allowing windows cd to boot from starting up computer?

---

### Post by Virtua-Touch on 2008-11-09
I did not use Wubi. I partitioned the 14 GB left on the hard drive with Ubuntu, and now I need to remove it.

---

### Post by bulldog on 2008-11-09
> **billgujie said:**
> hi,

saying if i need recover the windows MBR, do i format the linux partitions first then use windows install cd to perform recovery?

Because i tried to boot the windows install cd when both of two OS are on my computer it failed to boot, i guess its because the GRUB not allowing windows cd to boot from starting up computer?

GRUB has nothing to do with that.
You have to set boot from cd first in your BIOS.
The windows cd should start,you have to go to the recovery console and logon to your existing windows usual 1.
Than perform the command fixboot and/or fixmbr and GRUB will be deleted from the MBR.
GRUB will not do anything to stop you,for that matter.

---

### Post by bulldog on 2008-11-09
> **Virtua-Touch said:**
> I did not use Wubi. I partitioned the 14 GB left on the hard drive with Ubuntu, and now I need to remove it.

You can format this 14GB partition from within windows,so ubuntu is gone,but to remove GRUB you have to do as I explained earlier.

---

### Post by Virtua-Touch on 2008-11-09
Okay. Will do.

---

### Post by Virtua-Touch on 2008-11-10
Okay, well I found my Win98 SE disk and popped it in while running, and I clicked setup and it popped up the setup application. It never gave me a recovery option or thing. Because GRUB is installed, I do not know how to get into my Win98 BIOS to boot from disk. Could you give me an in-depth tutorial on how this can be accomplished?

---

