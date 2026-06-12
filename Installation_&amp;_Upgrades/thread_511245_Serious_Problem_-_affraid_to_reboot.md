---
title: "Serious Problem - affraid to reboot"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by hockman5 on 2007-07-27
My system:
   70 gig drive - WinXP
    5 gig drive - ubuntu

I was running the LiveCD and decided to install on the scsi2 drive (5 gig).
I noticed that my 70 gig drive (scsi 1)was partitioned with my windows partition, and two smaller partitions that I didn't know what there were. So I resized the Windows partition in make it larger and combined that three partitions into one. I then told the LiveCD to go ahead and install on the 5 gig drive. At the end of the installation, it came back with a serious grub error and it couldn't write grub to the boot sector. Now I am afraid that I have lost my bootability.
Previous to the installation, and after I combined the partitions on scsi1, I only received options to boot into Ubuntu. So the Windows boot has disappeard from grub. I loaded the WinXP cd and tried to recover the boot record using fixmbr and fixboot and the bootcfg commands. It didn't do anything. 
Any ideas on how to get my Winxp drive to boot up? It is accessible through Ubuntu so I know the drive is good. I guess I just messed up the boot record portion somehow.

Thanks,
:guitar:

---

### Post by Nick w on 2007-07-27
no fear soldier.

you can repair the master boot record. i had this issue before.


i unstalled ubuntu on a partion i was dual booting ubuntu then grub would fail so i couldnt boot at all

i found that if this happens load the recovery consol and boot in the CMD.  then type fixboot or fixmbr


DONE

:)

---

### Post by hockman5 on 2007-07-27
> **Nick w said:**
> no fear soldier.

you can repair the master boot record. i had this issue before.


i unstalled ubuntu on a partion i was dual booting ubuntu then grub would fail so i couldnt boot at all

i found that if this happens load the recovery consol and boot in the CMD.  then type fixboot or fixmbr


DONE

:)

If you notice in my post, that was the first thing I tried and it left me with no boot at all. 
Since then, I have booted back into LiveCD and then did the install again and it worked. Now, I have an option in grub to boot into Windows, but it doesn't work.
Thanks

---

### Post by hockman5 on 2007-07-28
Well I have tried everything but no success. I still can not boot into WinXP. I get grub error 18.
I do not know what else to do, nobody has offered me any support on the forum so I will give up and go back to Fedora I guess.

---

### Post by rillip on 2007-07-28
> **hockman5 said:**
> Well I have tried everything but no success. I still can not boot into WinXP. I get grub error 18.
I do not know what else to do, nobody has offered me any support on the forum so I will give up and go back to Fedora I guess.

Grub is grub.  Whether you have Fedora or Ubuntu, this issue will remain.

Just a quick Google gave me this:

Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. 

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem. 
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. 
[edit]
Tips

For an awesome resource for troubleshooting just about any Grub problem (on any OS), see this thread on Gentoo's forums: Gentoo Forums: Grub Error Collection

You can get the full article and links at [http://wiki.linuxquestions.org/wiki/GRUB]("http://wiki.linuxquestions.org/wiki/GRUB").  It has its own section on Grub error 18, sounds like this is more a bios problem than Grub.

---

