---
title: "Upgrade ubuntu 7.1 to 8.04 preserve grub in /boot"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by katapita on 2008-09-12
I have a dual boot system (Vista + Ubuntu).
I have grub installed in the first sector of the root (/) partition and not
in the MBR.  I have modified the vista bootloader with EasyBCD to allow me to boot into Vista or Linux.  
Will this be preserved when I upgrade ? 
Updates to 7.1 including the kernel update did not mess this.
Will grub be installed in the MBR by default when I upgrade ?
Is there a way to prevent it during the upgrade ?
Thanks.

---

### Post by caljohnsmith on 2008-09-13
> **katapita said:**
> I have a dual boot system (Vista + Ubuntu).
I have grub installed in the first sector of the root (/) partition and not
in the MBR.  I have modified the vista bootloader with EasyBCD to allow me to boot into Vista or Linux.  
Will this be preserved when I upgrade ? 
Updates to 7.1 including the kernel update did not mess this.
Will grub be installed in the MBR by default when I upgrade ?
Is there a way to prevent it during the upgrade ?
Thanks.
You should be perfectly OK with the upgrade; upgrading will not touch your MBR. But if you want to give yourself a warm fuzzy feeling knowing that you have a backup of the MBR in case something happens, you can back up the MBR with:
```
sudo dd if=/dev/[COLOR="Blue"]sda[/COLOR] bs=512 count=1 > ~/Desktop/MBR.bin
```
If your HDD is not sda, you'll need to change that, otherwise the above command will save a copy of your MBR to your desktop. :)

---

### Post by katapita on 2008-09-13
> **caljohnsmith said:**
> You should be perfectly OK with the upgrade; upgrading will not touch your MBR. But if you want to give yourself a warm fuzzy feeling knowing that you have a backup of the MBR in case something happens, you can back up the MBR with:
```
sudo dd if=/dev/[COLOR="Blue"]sda[/COLOR] bs=512 count=1 > ~/Desktop/MBR.bin
```
If your HDD is not sda, you'll need to change that, otherwise the above command will save a copy of your MBR to your desktop. :)
Thanks for the backup plan.  In case of a problem how would I restore the MBR (512 bytes?)

---

### Post by caljohnsmith on 2008-09-13
> **katapita said:**
> Thanks for the backup plan.  In case of a problem how would I restore the MBR (512 bytes?)
If at some point you want to restore the MBR, it is important to keep in mind that the first 446 bytes of the MBR are the boot loader portion, and the remaining bytes are for the HDD's partition table. In most cases you will just want to restore the MBR boot loader, and not the partition table, because you might have changed your HDD's partition scheme since you last saved your MBR. Therefore, to just restore the boot loader you would do:
```
sudo dd if=/path/to/MBR.bin of=/dev/[COLOR="Blue"]sda[/COLOR] bs=446 count=1
```
Again, make sure you use the correct HDD if it isn't sda.

---

