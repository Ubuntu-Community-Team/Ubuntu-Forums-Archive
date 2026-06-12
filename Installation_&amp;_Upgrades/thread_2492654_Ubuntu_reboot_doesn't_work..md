---
title: "Ubuntu reboot doesn't work."
date: 2023-11-18
forum: Installation &amp; Upgrades
---

### Post by aliamani on 2023-11-18
Hi. I have installed windows 11 and ubuntu 22.04 in dual boot. the boot loader of them are located in different efi partitions I can reboot from windows but I cannot restart or shutdown ubuntu. It gets stuck. Please help me  to repair it. Here is the report from boot repair:
[https://paste.ubuntu.com/p/67HgYJpVSC/](https://paste.ubuntu.com/p/67HgYJpVSC/)

---

### Post by TenPlus1 on 2023-11-19
Have you disabled fast boot in Windows 11 and in the bios ?

---

### Post by ajgreeny on 2023-11-19
I notice in your folder /etc/grub.d there are several **proxy** files which probably means you are, or have been, using Grub-Customiser.

This complicates repairing grub and the simplest way to help yourself may be to remove GC and then completely reinstall grub.

However, I have no personal experience of GC or repairing grub after it has caused problems  so before getting totally bogged down, have a search through the forum where you will find many users troubled by using GC and where possible solutions are mentioned,

There is also a long post in the  forums.linuxmint.com at [https://forums.linuxmint.com/viewtopic.php?f=42&t=319789](https://forums.linuxmint.com/viewtopic.php?f=42&t=319789) which might be helpful to you.
See also the warnings and information at [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

Most importantly, learn how to manage grub without GC; it's really not too complicated to make changes by editing text files in the system.

---

### Post by yancek on 2023-11-19
>  the boot loader of them are located in different efi partitions 

No, they aren't.  The EFI boot files for both windows and Ubuntu are on /dev/nvme0n1p1 which you can see in the boot repair output, lines 8-18.  Lines 42-48 show another vfat partition and line 161 indicates it is 244M.  So that second vfat partition is probably what you though would be a separate EFI parittion for Ubuntu which is/was not needed..  All the required EFI boot files for windows and ubuntu are on /dev/nvme0n1p1.  Partition 5 on that drive is useless/empty so should be deleted.  Line 236 shows your Ubuntu fstab file pointing to the EFI partition, /dev/nvme0n1p1 NOT to partition 5.

I"d agree with the post above about getting rid of Grub Customizer and reinstalling Grub to start with and see what happens.  Also, it would help if you could be more specific about what "it gets stuck" means.  Do see a warning/error message, do see a grub prompt (grub>), a black screen or ???

I imagine you read a tutorial indicating you needed an EFI partition to install a current Ubuntu but they neglected to inform readers this was not necessary if an EFI partition already existed.  Installing Linux on a machine with a windows EFI install willl not overwrite the boot files as was generally done with MBR installs of either system.  Separate directories are created on the EFI partition for each OS so that is not a problem.

---

### Post by MAFoElffen on 2023-11-20
> **aliamani said:**
> I can reboot from windows but I cannot restart or shutdown ubuntu. It gets stuck. Please help me  to repair it.
I have been hanging back, waiting...  ^^^That is not a booting problem.

I am not a fan of Grub Customizer. That "is" a problem just waiting to happen, but that is not remotely connected to your issue of not being able to reboot nor shutdown... It will be a problem eventually. Just not at the moment.

With that out of the way, if you look at the end of your journal entries on the last booted session, did it just stop at which message? Post the output of this, posted within CODE Tags:
```

journalctl -b 2 --g 'target' --no-pager | tail -n200

```

I would visit this bug report and  go to the link near the upper left and mark it as that it affects you: [https://bugs.launchpad.net/bugs/2036987](https://bugs.launchpad.net/bugs/2036987)

---

