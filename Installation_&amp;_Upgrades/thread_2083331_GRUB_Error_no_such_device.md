---
title: "GRUB Error: no such device"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by lemonchicken on 2012-11-12
```
error: no such device: abc123 
error: cannot get C/H/S values. 
error: you need to load the kernel first.  Press any key to continue ...
```Hello,

A while ago I splashed out on one of those revodrives, and having returned to Ubuntu, would like to dual boot Win7.

After removing Win7 and installing Ubuntu afresh on the drive, I found that the drive had been split in two.

Unfortunately the install didn't work, and I found myself reinstalling Windows on the drive.

I have Ubuntu installed on the second partition and grub loads but it won't boot with the error above.

Have tried boot-repair, mounting the drive and grub-update etc.


Are there any specific commands to fix this?? or anything that might work??


cheers and thanks,

:KS

---

### Post by lemonchicken on 2012-11-12
```
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sdb2
Found Ubuntu 12.10 (12.10) on /dev/sdd1
done
```The  issue must be with the kernel.. when I run grub-update, kernels for  12.04 (3.2..) show as installed but 12.10 (3.5..) is not.. 

How can I reinstall a kernel from another partition?

---

### Post by oldfred on 2012-11-12
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by lemonchicken on 2012-11-12
> **oldfred said:**
> Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Thanks Fred,

```
http://paste.ubuntu.com/1353903/
```

---

### Post by oldfred on 2012-11-12
It looks like you have the grub for 12.04 in every MBR. That probably was a default from Boot-Repair. But you really should have each system's boot loader in the drive the system is installed.
Or 12.04 in sda, Windows in sdb and 12.10 in sdd.

Two issues could be related to error. One is error in partition table which causes grub to fail on search to find correct partition to boot from and very large / (root) partition.

```
/dev/sdc3 ends after the last sector of /dev/sdc
```

You can run fixparts and see it it will update partition table.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

That may solve the issue. Try Using Boot-Repair's advanced option to install just one boot loader per drive for each different system. If not reinstall grub2's boot loader and Windows to the drive it is installed into:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you still get an error with 12.04, it can be because a a too large root. Grub seems to have an issue with very large root partitions. Boot-Repair will suggest a separate /boot. I normally suggest smaller / of 25GB and the rest as /home. Your choice.

---

